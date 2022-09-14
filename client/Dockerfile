# FROM node:12.18.3

# ENV SKIP_PREFLIGHT_CHECK=true

# WORKDIR /app

# COPY ["package.json", "package-lock.json", "./"]

# RUN npm install --production

# COPY . .

# EXPOSE 3000

# CMD ["npm", "start"]

FROM node:15-alpine3.10 as build
ENV NODE_ENV production
ENV SKIP_PREFLIGHT_CHECK true
ENV REACT_APP_PRODUCTION true
LABEL version="1.0"
LABEL description="This is the base docker image for prod frontend react app."
LABEL maintainer = ["abc@gmail.com", "anc@gmail.com"]

WORKDIR /app

COPY ["package.json", "./"]

RUN npm install --production

COPY . ./


RUN npm run build


# production environment
FROM nginx:1.19.10-alpine
COPY --from=build /app/build /usr/share/nginx/html

COPY --from=build /app/nginx/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80:80
EXPOSE 443:443
CMD ["nginx", "-g", "daemon off;"]
