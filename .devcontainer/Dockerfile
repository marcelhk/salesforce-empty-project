FROM salesforce/cli:latest-full

## Install python dependencies for CumulusCI
#RUN apt-get update \
#    && apt-get install -y --no-install-recommends \
#    python3.8 \
#    python3-pip \
#    python3-venv \
#    && rm -rf /var/lib/apt/lists/* \
#    && python3 -m pip install --user pipx \
#    && python3 -m pipx ensurepath

# Install PMD
ENV PMD_VERSION "7.0.0-rc4"
ENV PMD_DIR "/bin/pmd/"
RUN mkdir -p "${PMD_DIR}" \
    && wget -P /tmp/ https://github.com/pmd/pmd/releases/download/pmd_releases/${PMD_VERSION}/pmd-dist-${PMD_VERSION}-bin.zip \
    && unzip /tmp/pmd-bin-${PMD_VERSION}.zip -d /tmp \
    && rm /tmp/pmd-bin-${PMD_VERSION}.zip \
    && mv /tmp/pmd-bin-${PMD_VERSION}/* ${PMD_DIR}

## Install CumulusCI
#RUN ~/.local/bin/pipx install cumulusci

## Generate random 16 character encryption key for CumulusCI's local storage of sensitive information
#RUN touch ~/.profile && echo export CUMULUSCI_KEY=$(dd if=/dev/urandom bs=12 count=1 2>/dev/null | base64 | sed 's/=//g') >> ~/.profile
