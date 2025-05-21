# Data Science Project Template

This template is designed to jumpstart data science projects by providing a basic setup for database connections, data processing, and machine learning model development. It includes a structured folder organization for your datasets and a predefined set of Python packages required for most data science tasks.

## Structure

The project is organized as follows:

- **`src/app.py`** → Main Python script where your project will run.
- **`src/explore.ipynb`** → Notebook for exploration and testing. Once exploration is complete, migrate clean code to `app.py`.
- **`src/utils.py`** → Helper functions, such as database connections.
- **`requirements.txt`** → List of required Python packages.
- **`models/`** → Will contain your SQLAlchemy model classes.
- **`data/`** → Stores datasets in different stages:
  - **`data/raw/`** → Raw, unprocessed data.
  - **`data/interim/`** → Temporarily transformed data.
  - **`data/processed/`** → Data ready for analysis.

## ⚡ Initial Setup on Codespaces (Recommended)

No manual configuration is required, as **Codespaces is automatically set up** with the predefined files created by the academy. Just follow these steps:

1. **Wait for the environment to set itself up automatically.**
   - All necessary packages and the database will install themselves.
   - The automatically created `username` and `db_name` are stored in the **`.env`** file at the project root.
2. **Once Codespaces is ready, you can start working immediately.**

## 💻 Local Setup (Only if you cannot use Codespaces)

### Prerequisites

Make sure you have Python 3.11+ installed on your machine. You will also need `pip` to install Python packages.

### Installation

Clone the project repository to your local machine.

Navigate to the project directory and install the required Python packages:

```bash
pip install -r requirements.txt
```

### Create a Database (if needed)

Create a new database within your Postgres engine by customizing and running the following command:

```bash
$ psql -U postgres -c "DO \$\$ BEGIN 
    CREATE USER my_user WITH PASSWORD 'my_password'; 
    CREATE DATABASE my_database OWNER my_user; 
END \$\$;"
```

Connect to the Postgres engine to use your database, manipulate tables and data:

```bash
$ psql -U my_user -d my_database
```

Once inside PSQL, you’ll be able to create tables, query, insert, update or delete data, and much more!

### Environment Variables

Create a `.env` file in the root directory of the project to store your environment variables, such as your database connection string:

```makefile
DATABASE_URL="postgresql://<USER>:<PASSWORD>@<HOST>:<PORT>/<DB_NAME>"

# example
DATABASE_URL="postgresql://my_user:my_password@localhost:5432/my_database"
```

## Running the Application

To run the application, execute the `app.py` script from the root project directory:

```bash
python src/app.py
```

## Adding Models

To add SQLAlchemy model classes, create new Python script files inside the `models/` directory. These classes should be defined according to your database schema.

Example model definition (`models/example_model.py`):

```python
from sqlalchemy.orm import DeclarativeBase
from sqlalchemy import String
from sqlalchemy.orm import Mapped, mapped_column

Base = declarative_base()

class ExampleModel(Base):
    __tablename__ = 'example_table'
    id: Mapped[int] = mapped_column(primary_key=True)
    username: Mapped[str] = mapped_column(unique=True)
```

## Working with Data

You can place your raw datasets in the `data/raw` directory, intermediate datasets in `data/interim`, and processed datasets ready for analysis in `data/processed`.

To process data, you can modify the `app.py` script to include your data processing steps, using `pandas` for manipulation and analysis.

## Contributors

This template was built as part of the [Data Science and Machine Learning Bootcamp](https://4geeksacademy.com/us/coding-bootcamps/datascience-machine-learning) by 4Geeks Academy, created by [Alejandro Sanchez](https://twitter.com/alesanchezr) and many other contributors. Learn more about [4Geeks Academy Bootcamp programs](https://4geeksacademy.com/us/programs) here.

Other templates and resources like this can be found on the school’s GitHub page.
