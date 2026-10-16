
FROM mcr.microsoft.com/devcontainers/java:17-bookworm

ENV ANDROID_HOME=/opt/android-sdk
ENV PATH="${ANDROID_HOME}/cmdline-tools/latest/bin:${ANDROID_HOME}/platform-tools:${PATH}"

RUN apt-get update \
    && apt-get install -y --no-install-recommends curl unzip \
    && rm -rf /var/lib/apt/lists/* \
    && mkdir -p "$ANDROID_HOME/cmdline-tools" \
    && curl -fsSL \
      https://dl.google.com/android/repository/commandlinetools-linux-15859902_latest.zip \
      -o /tmp/android-tools.zip \
    && unzip -q /tmp/android-tools.zip -d /tmp \
    && mv /tmp/cmdline-tools "$ANDROID_HOME/cmdline-tools/latest" \
    && rm /tmp/android-tools.zip \
    && yes | sdkmanager --licenses > /dev/null

RUN sdkmanager --install \
      "platforms;android-30" \
      "build-tools;35.0.0" \
      "platform-tools" \
      "ndk;21.3.6528147" \
    && chown -R vscode:vscode "$ANDROID_HOME"
