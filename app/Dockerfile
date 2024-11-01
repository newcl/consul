# Start with the official Golang image
FROM golang:1.23-alpine AS builder

# Set the working directory
WORKDIR /app

# Copy go mod and sum files
# COPY go.mod go.sum ./

RUN test -f go.mod && cp go.mod ./ || echo "File not found, skipping copy"
RUN test -f go.sum && cp go.sum ./ || echo "File not found, skipping copy"


# Download all dependencies (use the cache)
# RUN go mod download

# Copy the source code
COPY . .

# Build the Go app`
RUN go build -o server

# Final stage: minimal image with only the compiled binary
FROM alpine:latest
WORKDIR /root/
COPY --from=builder /app/server .

# Expose port
EXPOSE 8080

# Command to run
CMD ["./server"]
