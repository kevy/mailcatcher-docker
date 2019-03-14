# Kevy Mailcatcher Docker Image
This is a containerized version of mailcatcher that will uses the same ruby version `2.3.4` as the app itself.

## Setup
This image can be run both in a stand-alone using `docker` or added to the container orchestration of an existing project using `docker-compose`.

#### Docker
```bash
# build image
docker build https://github.com/kevy/mailcatcher-docker.git -t mailcatcher

# start mailcatcher service
docker run -d -p ${port}:1080 --name mail mailcatcher

# stop mailcatcher service
docker container stop mail
```

#### Docker Compose
Add the following to your service block of `docker-compose.yaml`:

```bash
mail:
  container_name: kemp_mail
  image: github.com/kevy/mailcatcher-docker
  ports:
    - "${port}:1080"
```

## Usage

**Use** `SMTP` port `1025` in your development environment to send all mail to mailcatcher.

**View** the mailcatcher mailbox at `http://localhost:${port}` where `${port}` is the designated port number you chose to pass through to the mailcatcher container.