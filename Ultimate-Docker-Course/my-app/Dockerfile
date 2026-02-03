FROM node:24.13.0-alpine3.23
RUN addgroup app && adduser -S -G app app
USER app

WORKDIR /app

# Add steps to install dependencies first, so docker doesn't have to rebuild this layer every time
COPY --chown=app:app package*.json .
RUN npm install

# Copy other files. This overwrites package*, so make sure to change ownership again
# Because COPY runs as the root user by default
COPY --chown=app:app . .


ENV API_URL=http://api.myapp.com
EXPOSE 3000
# Shell form (docker executes this inside a separate shell). Usually /bin/sh
# CMD npm start

# Exec form (no need to spin up a new shell process)
# Good for executing ad-hoc instructions inside a container
# CMD ["npm", "start"]

# Entrypoint is better when you know exactly what program you want the container to start with
# It is also harder to override when calling docker run
# ENTRYPOINT [ "npm", "start" ]