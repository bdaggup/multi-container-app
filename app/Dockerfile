FROM node:24-alpine

WORKDIR /app/todos

RUN --mount=type=bind,source=package.json,target=package.json \
    --mount=type=bind,source=package-lock.json,target=package-lock.json \
    --mount=type=cache,target=/root/.npm \
    npm ci --include=dev

COPY .npmrc .

RUN npm install -g nodemon

COPY . .

RUN chown -R node:node /app/todos

USER node

EXPOSE 3000

CMD ["npm", "run", "dev"]