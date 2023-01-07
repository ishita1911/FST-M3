# Build Phase
FROM node:alpine as builder
WORKDIR /usr/app
COPY ./package.json .
RUN npm install
COPY . .
RUN npm run build

# Run Phase
FROM node:alpine
WORKDIR /usr/app
COPY package.json ./
RUN npm install
COPY --from=builder /usr/app/dist .
CMD ["node", "server.js"]