# chatgpt_telegram_bot_docker

docker-compose.yaml:
```yaml
version: "3"

services:
  mongo:
    container_name: chatgpt-mongo
    image: mongo:latest
    restart: always
    volumes:
      - ./db:/data/db

  chatgpt_telegram_bot:
    container_name: chatgpt
    image: ghcr.io/apocalypsor/chatgpt-telegram:latest
    command: python3 bot/bot.py
    restart: always
    volumes:
      - ./config/config.yaml:/code/config/config.yml:ro
      - ./config/config.env:/code/config/config.env:ro
    depends_on:
      - mongo
````
