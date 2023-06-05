# redis_in_django
<h1>Integrating Redis in Django | Learn how to integrate Redis in Django | Use Caching in Django</h1>  




Learn how to use Redis with Django. Cache data with Django to load pages faster with improved performance.I have explained how you can use Redis with Django in a fun way. Created one Django project to get things more familiar to you. What is Redis? - Redis is an in-memory data structure project implementing a distributed, in-memory key-value database with optional durability.  


To install Redis on a Mac, you can follow the steps below:

Open Terminal on your Mac. You can find it in the "Utilities" folder within the "Applications" folder, or you can use Spotlight to search for it.

Install Homebrew (a popular package manager for macOS) if you haven't already. Paste the following command into Terminal and press Enter:

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
Once Homebrew is installed, use the following command to install Redis:

brew install redis
After the installation is complete, start the Redis server by running the following command:

brew services start redis
This will start Redis as a background service, which means it will automatically run whenever you start your Mac.

To verify that Redis is running correctly, you can use the Redis command-line interface. Open a new Terminal window and run the following command:

redis-cli ping
If Redis is running properly, it will respond with "PONG."

Then add some setting in django project follow below code: 
Cache settings - 

CACHE_TTL = 60 * 1500

CACHES = {
    "default": {
        "BACKEND": "django_redis.cache.RedisCache",
        "LOCATION": "redis://127.0.0.1:6379/1",
        "OPTIONS": {
            "CLIENT_CLASS": "django_redis.client.DefaultClient"
        },
        "KEY_PREFIX": "example"
    }
}




Set Up a Virtual Environment (optional but recommended) Create a virtual environment to isolate the project dependencies:

python -m venv env

Activate the virtual environment:

For Windows: env\Scripts\activate For macOS/Linux: source env/bin/activate

Install Dependencies Install the project dependencies using pip:
pip install -r requirements.txt

Apply the database migrations: 
python manage.py makemigrations 
python manage.py migrate

Create a superuser to access the admin interface:

python manage.py createsuperuser
Run the Server Start the Django development server:

python manage.py runserver
Open your web browser and go to http://localhost:8000/ to access the application.