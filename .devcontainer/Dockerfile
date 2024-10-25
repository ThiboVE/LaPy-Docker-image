# Use a base image with Python 3.12 pre-installed
FROM python:3.10-slim

# Change workspace dir to the name of your directory
ARG WORKSPACE_DIR=/1ste-Master

# Install dependencies and tools for LaTeX
RUN apt-get update && apt-get install -y \
    texlive-latex-base \
    texlive-latex-extra \
    texlive-latex-recommended \
    latexmk \
    git \
    wget \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install pipenv or any additional Python tools as needed
RUN pip install --upgrade pip

# Copy the requirements.txt file into the container
COPY .devcontainer/requirements.txt /tmp/requirements.txt

# Install the Python dependencies listed in requirements.txt
RUN pip install -r /tmp/requirements.txt

# Set a working directory in the container (project root)
WORKDIR ${WORKSPACE_DIR}

COPY . ${WORKSPACE_DIR}/

# Optionally install VSCode server for VSCode remote containers (optional)
# RUN wget -qO- https://aka.ms/install-vscode-server/setup.sh | bash

# Expose ports for VSCode remote development, if needed (optional)
# EXPOSE 8080

# Set default entry point (bash) so you can interact with the container
CMD ["bash"]
