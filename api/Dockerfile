# syntax=docker/dockerfile:1

FROM python:3-alpine


# Create a working directory for Docker to use
WORKDIR /app



# Copy any file dependecies to the image
COPY requirements.txt .

# Install app dependencies
RUN \
 apk add --no-cache postgresql-libs && \
 apk add --no-cache --virtual .build-deps gcc musl-dev postgresql-dev && \
 python3 -m pip install -r requirements.txt

# Bundle app source
COPY . .
EXPOSE 8000
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]



