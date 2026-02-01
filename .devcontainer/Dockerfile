FROM texlive/texlive:latest-full

LABEL maintainer="DevContainer LaTeX FR"
LABEL description="Environnement LaTeX pour articles en français avec bibliographie"

# Création d'un utilisateur non-root
# Note: L'image texlive utilise déjà UID 1000 pour l'utilisateur "texlive"
ARG USERNAME=vscode
ARG USER_UID=1001
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME \
    && rm -rf /var/lib/apt/lists/*

# Outils système utiles et biber (gestionnaire de bibliographie)
RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    make \
    biber \
    default-jre-headless \
    && rm -rf /var/lib/apt/lists/*

# Vérification de l'installation
RUN pdflatex --version && biber --version

# Passage à l'utilisateur non-root
USER $USERNAME
WORKDIR /home/$USERNAME
