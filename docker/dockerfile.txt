# Utilisez une image de base de Jupyter
FROM jupyter/scipy-notebook:latest

# Définir le répertoire de travail dans le conteneur
WORKDIR /app

# Copier le fichier requirements.txt et installer les dépendances
COPY requirements.txt /app/requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Copier votre fichier Jupyter Notebook
COPY credit_scoring.ipynb /app/credit_scoring.ipynb

# Exposer le port sur lequel Jupyter Notebook s'exécute
EXPOSE 8888

# Commande pour démarrer Jupyter Notebook
CMD ["start-notebook.sh", "--NotebookApp.token=''"]
