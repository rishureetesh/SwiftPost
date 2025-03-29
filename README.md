# SwiftPost

**SwiftPost** is a fast and efficient email delivery system that handles email tasks in the background without slowing down your app. Built using **Flask**, **Celery**, and **Redis**, SwiftPost ensures smooth, asynchronous email handling for tasks like welcome emails, notifications, and newsletters.

## Features
- Asynchronous email sending using Celery
- Reliable task queue with Redis as the broker
- Easy integration into Flask-based applications
- Lightweight and scalable

## Technologies Used
- **Flask** - Lightweight web framework
- **Celery** - Asynchronous task queue
- **Redis** - Message broker for Celery
- **Docker** - Containerization for easy deployment

## Getting Started

### Prerequisites
- Python 3.x
- Redis installed (or use Docker)
- Celery and Redis dependencies

### Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/your-username/SwiftPost.git
    cd SwiftPost
    ```

2. Install the required dependencies:
    ```bash
    pip install -r requirements.txt
    ```

3. Start the Redis server (if not using Docker):
    ```bash
    redis-server
    ```

4. Run the Flask app:
    ```bash
    python app.py
    ```

5. In another terminal, start the Celery worker:
    ```bash
    celery -A tasks worker --loglevel=info
    ```

6. You can now test sending emails by visiting the `/register` route (or any route you have set up) to simulate email tasks!

### Docker Setup

1. Build and start the Docker containers:
    ```bash
    docker-compose up --build
    ```

2. Access the app at `http://localhost:5000` and watch SwiftPost handle the background email tasks seamlessly!

## Usage

Once your app is running, any email task (e.g., welcome email after user registration) will be sent in the background, ensuring a smooth and responsive user experience.

### Example:
To send a welcome email, just call the Celery task from within your Flask app:
```python
from tasks import send_welcome_email

send_welcome_email.delay(user_email)
