FROM python:3.11

# Set environment variable to ensure output is sent straight to terminal
ENV PYTHONUNBUFFERED=1

# Set the working directory in the container
WORKDIR /app

# Upgrade pip and install Poetry
RUN pip install --upgrade pip "poetry==2.1.4"

# Configure Poetry to not create a virtual environment
RUN poetry config virtualenvs.create false --local

# Copy the dependency files
COPY pyproject.toml poetry.lock ./

# Install the dependencies
RUN poetry install --no-root

# Copy the application code
COPY mysite .

# Command to run the application
CMD ["gunicorn", "mysite.wsgi:application", "--bind", "0.0.0.0:8000"]