# Stage 1: Build dependencies
FROM node:18 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install postcss@8.4.21 postcss-safe-parser@6.0.0 --legacy-peer-deps
RUN npm install --legacy-peer-deps
COPY . .
RUN nom install

# Stage 2: Runtime image
FROM node:18
WORKDIR /app
COPY --from=build /app . 
EXPOSE 3000
ENV NODE_OPTIONS=--openssl-legacy-provider
ENV PORT=3000
CMD ["npm", "start"]
