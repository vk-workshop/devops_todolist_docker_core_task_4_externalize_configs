# DevOps Todo List Application

## Getting Started

### Clone the Repository
```bash
git clone https://github.com/vk-workshop/devops_todolist_docker_core_task_4_externalize_configs.git
cd devops_todolist_docker_core_task_4_externalize_configs
```

### Build and Run the Application
```bash
docker-compose up -d
```

Access the application at [http://localhost:8080/todolist/1/](http://localhost:8080/todolist/1/).

## Database Configuration
The database configuration is externalized using environment variables. Below are the required environment variables for MySQL:

```yaml
environment:
  - DB_ENGINE=mysql.connector.django
  - DB_NAME=app_db
  - DB_USER=app_user
  - DB_PASSWORD=1234
  - DB_HOST=mysql
  - DB_PORT=3306
```

### Django `DATABASES` Settings
The application uses the following `DATABASES` configuration in Django:

```python
DATABASES = {
    'default': {
        'ENGINE': os.getenv('DB_ENGINE', 'django.db.backends.mysql'),
        'NAME': os.getenv('DB_NAME', 'todolist'),
        'USER': os.getenv('DB_USER', 'user'),
        'PASSWORD': os.getenv('DB_PASSWORD', 'password'),
        'HOST': os.getenv('DB_HOST', 'localhost'),
        'PORT': os.getenv('DB_PORT', '3306'),
    }
}
