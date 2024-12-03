# Use ubuntu as the base image
FROM ubuntu:latest

# Install dependencies and Node.js
RUN apt-get update && apt-get install -y curl bash && curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && apt-get install -y nodejs && rm -rf /var/lib/apt/lists/* && apt-get clean && apt-get autoclean

# Set environment variables if any
ENV VAR1 ""

# Create working directory and assign rights
RUN mkdir -p /home/workingdir && chmod -R 755 /home/workingdir

# Set the working directory inside the container
WORKDIR /home/workingdir

# Copy your application files to the image
COPY . /home/workingdir

# Install Node.js dependencies
RUN npm install

# Make sure the script is executable
RUN chmod +x /home/workingdir/entrypoint.sh

# Expose necessary ports (if required by your app)
EXPOSE 8080

# Define the command to run the application
ENTRYPOINT ["/home/workingdir/entrypoint.sh"]