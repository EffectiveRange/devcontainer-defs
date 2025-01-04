# FROM effectiverange/er-devc-amd64:latest
FROM mcr.microsoft.com/devcontainers/typescript-node:1-22-bookworm

ARG USERNAME=vscode
# ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID


# [Optional] Uncomment this section to install additional vcpkg ports.
# RUN su vscode -c "${VCPKG_ROOT}/vcpkg install <your-port-name-here>"
# Print the values of the variables
RUN echo "USERNAME: $USERNAME" \
    && echo "USER_UID: $USER_UID" \
    && echo "USER_GID: $USER_GID"
# Create the user and get ownership of /opt/cross for package installation
# Create the user and get ownership of /opt/cross for package installation
RUN if ! id -u $USERNAME > /dev/null 2>&1; then useradd -s /bin/bash -m $USERNAME; fi \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME
# Create the user and get ownership of /opt/cross for package installation
# RUN groupadd --gid $USER_GID $USERNAME \
#     && useradd -s /bin/bash --uid $USER_UID --gid $USER_GID -m $USERNAME \
#     && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
#     && chmod 0440 /etc/sudoers.d/$USERNAME

# RUN groupadd $USERNAME \
#     && useradd -s /bin/bash  -m $USERNAME \
#     && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
#     && chmod 0440 /etc/sudoers.d/$USERNAME
# RUN chown -R $USERNAME:$USERNAME /opt/debs
# RUN [ -f  /etc/schroot/chroot.d/buildroot ] && sed -ri "s/(users=.*)/\1,$USERNAME/g" /etc/schroot/chroot.d/buildroot || true

# ********************************************************
# * Anything else you want to do like clean up goes here *
# ********************************************************
RUN npm install -g @angular/cli

# [Optional] Set the default user. Omit if you want to keep the default as root.
USER $USERNAME    
