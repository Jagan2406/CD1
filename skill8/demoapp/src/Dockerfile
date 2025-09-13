FROM node:20
WORKDIR /docker 
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 5111
CMD ["npm", "run", "dev", "--", "--host", "--port", "5111"]  