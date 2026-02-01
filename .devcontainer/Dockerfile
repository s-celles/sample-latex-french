FROM texlive/texlive:latest-medium

LABEL maintainer="DevContainer LaTeX FR"
LABEL description="Environnement LaTeX pour articles en français avec bibliographie"

# Création d'un utilisateur non-root
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME \
    && rm -rf /var/lib/apt/lists/*

# Installation des paquets LaTeX supplémentaires pour le français et la bibliographie
RUN tlmgr install \
    # Support français
    babel-french \
    hyphen-french \
    # Bibliographie moderne
    biblatex \
    biber \
    biblatex-ieee \
    biblatex-apa \
    # Polices et typographie
    fontspec \
    unicode-math \
    microtype \
    # Articles et mise en page
    geometry \
    fancyhdr \
    titlesec \
    enumitem \
    # Tableaux et figures
    booktabs \
    multirow \
    float \
    caption \
    subcaption \
    graphicx \
    # Maths et sciences
    amsmath \
    amssymb \
    mathtools \
    siunitx \
    # Code et algorithmes
    listings \
    algorithm2e \
    # Liens et références
    hyperref \
    cleveref \
    # Divers utiles
    csquotes \
    xcolor \
    lipsum \
    todonotes \
    appendix

# Outils système utiles
RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    make \
    && rm -rf /var/lib/apt/lists/*

# Vérification de l'installation
RUN lualatex --version && biber --version

# Passage à l'utilisateur non-root
USER $USERNAME
WORKDIR /home/$USERNAME
