# Create a docker image with MiniConda
FROM continuumio/miniconda3

# Create a new directory
WORKDIR /mainImage

# Coppy the environment file to the container
COPY environment.yml .

# Update the conda
RUN conda update -n base -c defaults conda

# Create a new environment with the environment file
RUN conda install pytorch torchvision torchaudio pytorch-cuda=11.8 -c pytorch -c nvidia

# Activate the environment
SHELL ["conda", "run", "-n", "PyTorch", "/bin/bash", "-c"]

# Open the port 8080
EXPOSE 8080

# Run the Jupyter Notebook
CMD ["conda", "run", "-n", "PyTorch", "jupyter", "notebook", "--ip=0.0.0.0", "--port=8080", "--no-browser", "--allow-root"]
