FROM flimzy/gopherjs

# Install gometalinter
RUN go get -u gopkg.in/alecthomas/gometalinter.v2 && gometalinter.v2 --install

# Flashback-specific deps
RUN npm install -g browserify cordova uglify-js
RUN go get -u github.com/jteeuwen/go-bindata/...

# JDK dependencies
RUN apt-get install -y openjdk-8-jdk gradle

# Android SDK
ENV ANDROID_HOME /opt/android-sdk
ENV PATH ${PATH}:${ANDROID_HOME}/emulator:${ANDROID_HOME}/tools:${ANDROID_HOME}/platform-tools:${ANDROID_HOME}/tools/bin

RUN mkdir -p ${ANDROID_HOME} && cd ${ANDROID_HOME} && \
    wget -q https://dl.google.com/android/repository/sdk-tools-linux-3859397.zip -O android-sdk.zip && \
    unzip android-sdk.zip && \
    rm android-sdk.zip

# 19 = Android 4.4/KitKat
# 26 = Android 8.0/Oreo
RUN sdkmanager --update && yes | sdkmanager "platforms;android-26" "build-tools;26.0.3" "extras;android;m2repository"
# RUN sdkmanager --update && yes | sdkmanager "platforms;android-19" "build-tools;19.1.0" "extras;android;m2repository"
