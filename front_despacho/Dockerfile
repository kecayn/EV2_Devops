# Etapa 1: Usa una imagen de node como base para compilar
FROM node:20-alpine AS build
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm install
COPY . .
RUN npm run build

# Etapa 2: Usar una imagen de nginx para servir el contenido estático
FROM nginx:1.19.0-alpine
COPY --from=build /app/dist/ /usr/share/nginx/html
EXPOSE 80