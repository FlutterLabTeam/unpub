# Use the Dart official image as a base
FROM dart:stable

# Set the working directory
WORKDIR /app

# Copy the pubspec files and get dependencies
COPY pubspec.* ./

# Get dependencies
RUN dart pub get

# Copy the rest of the application code
COPY . .

# Ensure the main Dart file is compiled
RUN dart pub get --offline
RUN dart compile exe bin/unpub.dart -o bin/server

# Expose the port the app runs on
EXPOSE 8080

# Run the compiled server
CMD ["./bin/server"]
