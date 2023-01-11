FROM salesforce/salesforcedx:latest-full

## Install python dependencies for CumulusCI
#RUN apt-get update \
#    && apt-get install -y --no-install-recommends \
#    python3.8 \
#    python3-pip \
#    python3-venv \
#    && rm -rf /var/lib/apt/lists/* \
#    && python3 -m pip install --user pipx \
#    && python3 -m pipx ensurepath

# Ensure that NODE_ENV is "development"
ENV NODE_ENV=development

# Install PMD
ENV PMD_VERSION "6.44.0"
ENV PMD_DIR "/bin/pmd/"
RUN mkdir -p "${PMD_DIR}" \
    && wget -P /tmp/ https://github.com/pmd/pmd/releases/download/pmd_releases%2F${PMD_VERSION}/pmd-bin-${PMD_VERSION}.zip \
    && unzip /tmp/pmd-bin-${PMD_VERSION}.zip -d /tmp \
    && rm /tmp/pmd-bin-${PMD_VERSION}.zip \
    && mv /tmp/pmd-bin-${PMD_VERSION}/* ${PMD_DIR}

# Install the Prettier plugin for Apex
RUN npm install --global prettier prettier-plugin-apex

# Install the sfdx-lwc-jest
RUN npm install --global @salesforce/sfdx-lwc-jest

## Install CumulusCI
#RUN ~/.local/bin/pipx install cumulusci

## Generate random 16 character encryption key for CumulusCI's local storage of sensitive information
#RUN touch ~/.profile && echo export CUMULUSCI_KEY=$(dd if=/dev/urandom bs=12 count=1 2>/dev/null | base64 | sed 's/=//g') >> ~/.profile
