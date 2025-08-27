FROM python:3.11-slim

ENV PYTHONUNBUFFERED=1

WORKDIR /app

RUN pip install --upgrade pip \
    && pip install "poetry==2.1.4"

# Configure Poetry to not create virtual environments
RUN poetry config virtualenvs.create false --local

COPY pyproject.toml poetry.lock ./

RUN poetry install --no-interaction --no-ansi

COPY . .

CMD ["gunicorn", "mysite.wsgi:application", "--bind", "0.0.0.0:8000"]
