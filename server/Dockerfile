FROM node:lts-alpine
ENV NODE_ENV=production
ENV CONTAINERS=true
WORKDIR /usr/src/app
COPY ["package.json", "package-lock.json*", "npm-shrinkwrap.json*", "./"]
RUN npm install --production --silent && mv node_modules ../
COPY . .

# RUN mkdir /etc/letsencrypt
# COPY letsencrypt/live/topatol.com/fullchain.pem /etc/letsencrypt
# COPY letsencrypt/live/topatol.com/privkey.pem /etc/letsencrypt
EXPOSE 5000
EXPOSE 5443
RUN chown -R node /usr/src/app
USER node
CMD ["npm", "start"]
