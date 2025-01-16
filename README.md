# Dockerfile Bug: Missing requirements.txt

This repository demonstrates a common error in Dockerfiles: attempting to install dependencies from a `requirements.txt` file that doesn't exist in the build context.  This leads to a build failure.

The original `Dockerfile` attempts to install Python packages, but the `requirements.txt` file is missing.  The solution demonstrates the correct way to include and manage dependencies.

## Bug

The `Dockerfile` in this repository will fail to build because the `requirements.txt` file, referenced in the `RUN` instruction, is missing.  This is a common oversight when creating Docker images.

## Solution

The `Dockerfile_solution` demonstrates the corrected version.  It includes a sample `requirements.txt` file and ensures the file is copied into the image before attempting the installation.

To reproduce the bug and then the solution:

1. Clone this repository.
2. Try building the original Dockerfile: `docker build -t buggy-app .` (This will fail)
3. Build the solution Dockerfile: `docker build -t fixed-app -f Dockerfile_solution .` (This will succeed)