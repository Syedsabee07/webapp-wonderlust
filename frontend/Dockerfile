# NORMAL FILE

#FROM node:21

#WORKDIR /app

#COPY . .

#RUN npm i

#COPY .env.sample .env.local

#EXPOSE 5173

#CMD ["npm", "run", "dev","--","--host"]




# MULTI-STAGE-DOCKERFILE

# Base image for frontend
FROM node:21 AS frontend-builder

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install required dependencies
RUN npm install

# Copy the rest of the application code to the working directory
COPY . .


# ------------------Stage-2 -----------------

#Base image for frontend
FROM node:21-slim

# Set the working directory inside the container
WORKDIR /app

#Copy build asset and dependencies fom frontend-builder stage
COPY --from=frontend-builder /app .

#Copy the env.sample file to .env file
COPY .env.sample .env.local

# Expose the port the app runs on
EXPOSE 5173

# Command to start the backend server
CMD ["npm", "run", "dev", "--", "--host"]
