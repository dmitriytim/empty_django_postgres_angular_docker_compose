# Используйте официальный образ Node.js
#FROM --platform=$BUILDPLATFORM node:18 as builder
FROM  node:20 as builder

# Устанавливаем рабочую директорию внутри контейнера
WORKDIR /app

# Копируем package.json и package-lock.json в контейнер
COPY package*.json ./

# Устанавливаем зависимости
#RUN npm install
RUN npm install -g @angular/cli --force


# Копируем все файлы из папки проекта в контейнер
COPY . .
RUN npm install --force
#CMD ["bash"]
CMD ["ng", "serve", "--host", "0.0.0.0", "--port", "4200", "--disable-host-check"]

