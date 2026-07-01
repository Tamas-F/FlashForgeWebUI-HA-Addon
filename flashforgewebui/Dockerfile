FROM node:20-alpine

WORKDIR /app

RUN apk add --no-cache git \
    && git clone https://github.com/Parallel-7/FlashForgeWebUI.git . \
    && npm install \
    && npm run build

ENV DATA_DIR=/data
EXPOSE 3000

CMD ["npm", "start"]
