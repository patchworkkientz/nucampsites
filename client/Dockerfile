FROM node:12.18.3

ENV SKIP_PREFLIGHT_CHECK=true

WORKDIR /app

COPY ["package.json", "package-lock.json", "./"]

RUN npm install --production

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
