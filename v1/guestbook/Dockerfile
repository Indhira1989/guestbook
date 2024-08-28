# Stage 1: Build the Go application
FROM golang:1.20 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy the source code
COPY . .

# Build the Go application
RUN go build -o guestbook main.go

# Stage 2: Create a minimal image for running the application
FROM alpine:latest

# Set the working directory inside the container
WORKDIR /root/

# Copy the built binary from the previous stage
COPY --from=build /app/guestbook .

# Set executable permissions
RUN chmod +x guestbook

# List files and permissions for debugging
RUN ls -l

# Expose the port the app runs on
EXPOSE 8080

# Run the Go application
CMD ["./guestbook"]