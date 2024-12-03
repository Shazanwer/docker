# Use the redhat universal base image
FROM redhat/ubi9-minimal:9.5@sha256:8b6978d555746877c73f52375f60fd7b6fd27d6aca000eaed27d0995303c13de

# Install dependencies and Node.js
RUN microdnf -y install dnf && dnf -y install bash && curl -sL https://rpm.nodesource.com/setup_20.x | bash - && dnf -y install nodejs && dnf clean all && rm -rf /var/cache/dnf

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