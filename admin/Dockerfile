# Pull base image
FROM python:3.11.5-slim-bullseye

RUN apt-get update && apt-get install -y \
  apt-utils \
  iputils-ping \
  binutils \
  libproj-dev \
  gdal-bin \
  python3-tk \
  netcat && \
  apt-get clean
# Set environment variables
ENV PIP_DISABLE_PIP_VERSION_CHECK 1
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Set work directory
WORKDIR /code

# Install dependencies
COPY ./requirements.txt .
RUN pip install -r requirements.txt

# Copy project
COPY . .
# Копируем wait-for-it.sh и устанавливаем права на выполнение
COPY ./wait-for-it.sh /usr/local/bin/wait-for-it.sh
RUN chmod +x /usr/local/bin/wait-for-it.sh
CMD ["sh", "-c", "/usr/local/bin/wait-for-it.sh db -- python manage.py migrate && python manage.py runserver 0.0.0.0:8000"]
