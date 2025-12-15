# 🎓 Academia Dev Python - Management System

Complete management system for students, courses and enrollments developed with Django and Django Rest Framework.

## 📋 About the Project

This project was developed as part of the technical challenge for the Python/Django development internship position. The system allows complete management of a course academy, including student registration, courses, enrollments and financial control.

## Technologies

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![DjangoREST](https://img.shields.io/badge/DJANGO-REST-ff1709?style=for-the-badge&logo=django&logoColor=white&labelColor=gray)
![PostgreSQL](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![HTML](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white)

## ✨ Features

### 📝 Registration
- **Students**: Name, email, CPF and enrollment date
- **Courses**: Name, workload, price and status (active/inactive)
- **Enrollments**: Relationship between students and courses with payment control

### 💰 Financial
- Payment status control (paid/pending)
- Total owed per student
- Total paid per student
- Complete financial reports

### 📊 HTML Reports
- General dashboard with statistics
- Complete history of each student
- Student list with financial information
- Most popular courses

### 🔌 REST API
Complete endpoints for:
- Students CRUD (`/api/alunos/`)
- Courses CRUD (`/api/cursos/`)
- Enrollments CRUD (`/api/matriculas/`)
- Reports via JSON
- Queries with Raw SQL

### 🗄️ Raw SQL
- `meu_database.sql` file with database structure
- Endpoints using raw SQL queries with JOIN and aggregations
- Optimized queries for complex reports

## 📁 Project Structure

```
python/
├── academia_dev/           # Project settings
│   ├── settings.py        # General settings
│   ├── urls.py           # Main URLs
│   └── wsgi.py           # WSGI config
├── core/                  # Main app
│   ├── models.py         # Models (Student, Course, Enrollment)
│   ├── serializers.py    # DRF Serializers
│   ├── views.py          # Views and ViewSets
│   ├── admin.py          # Django Admin config
│   └── urls.py           # App URLs
├── templates/            # HTML templates
│   ├── base.html        # Base template
│   └── core/            # Core templates
│       ├── dashboard.html
│       ├── aluno_lista.html
│       └── aluno_historico.html
├── Dockerfile           # Docker configuration
├── docker-compose.yml   # Docker orchestration
├── requirements.txt     # Python dependencies
├── meu_database.sql    # Database SQL schema
├── manage.py           # Django manager
└── README.md          # This file
```

## 🛠️ How to Run the Project

### Option 1: With Docker (Recommended)

### ⚡ Quick Start

**Recommended**: Use Docker for the easiest setup! No need to install PostgreSQL, Python packages, or configure anything manually. Just run:
```bash
docker-compose up --build
```
Everything will be automatically configured and ready to use! 🚀

### ⚡ Steps

```bash
# Clone the repository
git clone https://github.com/mbdsaraiva/Academia-dev-python.git
cd Academia-dev-python

# Run with Docker Compose
docker-compose up --build

# Access in browser
http://localhost:8000
```

Docker will:
- Install all dependencies
- Configure PostgreSQL
- Run migrations
- Create superuser (admin/admin123)
- Start the server

### Option 2: Local (without Docker)

#### Prerequisites
- Python 3.12+
- PostgreSQL 16+
- pip

#### Installation Steps

```bash
# Clone the repository
git clone https://github.com/mbdsaraiva/Academia-dev-python.git
cd Academia-dev-python

# Create virtual environment
python -m venv venv

# Activate virtual environment
# On Linux/Mac:
source venv/bin/activate
# On Windows:
venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Create database in PostgreSQL
createdb academia_dev

# Configure environment variables (or edit settings.py)
export POSTGRES_DB=academia_dev
export POSTGRES_USER=postgres
export POSTGRES_PASSWORD=postgres
export POSTGRES_HOST=localhost
export POSTGRES_PORT=5432

# Run migrations
python manage.py makemigrations
python manage.py migrate

# Create superuser
python manage.py createsuperuser

# Collect static files
python manage.py collectstatic

# Start development server
python manage.py runserver
```

## 🌐 Accessing the System

After starting the server, access:

- **Homepage/Dashboard**: http://localhost:8000/
- **Django Admin**: http://localhost:8000/admin/
- **REST API Root**: http://localhost:8000/api/
- **Students List**: http://localhost:8000/alunos/

### Default Credentials (if using Docker)
- **Username**: admin
- **Password**: admin123

## 📡 API Endpoints

### Students
- `GET /api/alunos/` - List all students
- `POST /api/alunos/` - Create new student
- `GET /api/alunos/{id}/` - Get student details
- `PUT /api/alunos/{id}/` - Update student (full)
- `PATCH /api/alunos/{id}/` - Update student (partial)
- `DELETE /api/alunos/{id}/` - Delete student
- `GET /api/alunos/{id}/matriculas/` - Student enrollments
- `GET /api/alunos/{id}/financeiro/` - Student financial summary

### Courses
- `GET /api/cursos/` - List all courses
- `POST /api/cursos/` - Create new course
- `GET /api/cursos/{id}/` - Get course details
- `PUT /api/cursos/{id}/` - Update course (full)
- `PATCH /api/cursos/{id}/` - Update course (partial)
- `DELETE /api/cursos/{id}/` - Delete course
- `GET /api/cursos/{id}/matriculas/` - Course enrollments
- `GET /api/cursos/{id}/estatisticas/` - Course statistics

### Enrollments
- `GET /api/matriculas/` - List all enrollments
- `POST /api/matriculas/` - Create new enrollment
- `GET /api/matriculas/{id}/` - Get enrollment details
- `PUT /api/matriculas/{id}/` - Update enrollment (full)
- `PATCH /api/matriculas/{id}/` - Update enrollment (partial)
- `DELETE /api/matriculas/{id}/` - Delete enrollment
- `POST /api/matriculas/{id}/marcar_pago/` - Mark as paid
- `POST /api/matriculas/{id}/marcar_pendente/` - Mark as pending
- `GET /api/matriculas/resumo_financeiro/` - Financial summary

### Raw SQL Reports
- `GET /api/relatorio-sql/` - Complete report using raw SQL
- `GET /api/cursos-populares-sql/` - Popular courses using raw SQL

## 📊 Database Schema

The complete database schema is available in the `meu_database.sql` file, including:
- Table structures with appropriate types
- Primary and foreign keys
- Indexes for performance
- Constraints and validations
- Example queries with JOINs and aggregations

## 🧪 Testing the API

### Using cURL

```bash
# List students
curl http://localhost:8000/api/alunos/

# Create student
curl -X POST http://localhost:8000/api/alunos/ \
  -H "Content-Type: application/json" \
  -d '{"nome":"John Doe","email":"john@email.com","cpf":"12345678901","data_ingresso":"2024-01-15"}'

# Get financial summary
curl http://localhost:8000/api/matriculas/resumo_financeiro/
```

### Using the Browsable API

Django Rest Framework provides a web interface for testing APIs:
- Access http://localhost:8000/api/
- Navigate through endpoints
- Use the HTML forms to create/update data

## 🐳 Docker Commands

```bash
# Start containers
docker-compose up

# Start in background
docker-compose up -d

# View logs
docker-compose logs -f

# Stop containers
docker-compose down

# Stop and remove volumes (clears database)
docker-compose down -v

# Rebuild containers
docker-compose up --build

# Execute command in container
docker-compose exec web python manage.py migrate

# Access container shell
docker-compose exec web bash
```

## 📝 Notes

### Challenge Requirements ✅

All mandatory requirements were implemented:

- ✅ Student registration (name, email, CPF, enrollment date)
- ✅ Course registration (name, workload, price, status)
- ✅ Enrollment system with payment control
- ✅ Financial control (total owed, total paid)
- ✅ HTML reports (student history, general dashboard)
- ✅ Complete REST API with DRF
- ✅ Raw SQL queries with JOIN and aggregations
- ✅ `meu_database.sql` file with schema
- ✅ Docker and docker-compose configuration
- ✅ PostgreSQL as database
- ✅ Complete README with instructions

### Design Decisions

- Used Django Admin for quick data management
- Clean and modern HTML interface for reports
- RESTful API following best practices
- Proper database normalization
- Optimized queries with indexes
- Comprehensive error handling and validations

## 👨‍💻 Author

**Matheus Saraiva**

Developed as part of the technical challenge for the Python/Django Developer Internship position - 2026.1
