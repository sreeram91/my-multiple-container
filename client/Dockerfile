FROM node:16-alpine AS builder
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
CMD ["npm", "run", "build"]

FROM nginx
COPY ./nginx/default.conf /etc/nginx/conf.d/default/conf
EXPOSE 3000
COPY --from=builder /app/build /use/share/nginx/html