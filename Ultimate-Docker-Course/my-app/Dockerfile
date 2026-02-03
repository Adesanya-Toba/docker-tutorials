FROM node:24.13.0-alpine3.23
WORKDIR /app
COPY . .

RUN addgroup app && adduser -S -G app app
# Change ownership of working directory before setting the USER
RUN chown -R app:app /app
USER app

RUN npm install
ENV API_URL=http://api.myapp.com
EXPOSE 3000
# Shell form (docker executes this inside a separate shell). Usually /bin/sh
# CMD npm start

# Exec form (no need to spin up a new shell process)
# Good for executing ad-hoc instructions inside a container
CMD ["npm", "start"]

# Entrypoint is better when you know exactly what program you want the container to start with
# It is also harder to override when calling docker run
# ENTRYPOINT [ "npm", "start" ]