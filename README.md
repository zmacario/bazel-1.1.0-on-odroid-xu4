# Bazel-1.1.0-on-ODROID-XU4
## How to build Bazel 1.1.0 from scratch (bootstrapping) and install it on ODROID-XU4 + Ubuntu 18.04.3 LTS (Bionic Beaver).

### 1. Let's start by updating ODROID Linux with the following commands in the terminal window:
```bash
sudo apt update
sudo apt upgrade
```
### 2. Install the packages bellow:
```bash
sudo apt -y install build-essential openjdk-8-jdk python zip unzip
```
Important: You must ensure OpenJDK v8 is the default for your system during the following steps.
### 3. Download official Bazel 1.1.0 zipped source file:
```bash
sudo wget https://github.com/bazelbuild/bazel/releases/download/1.1.0/bazel-1.1.0-dist.zip
```
### 4. Unzip downloaded file:
```bash
sudo unzip bazel-1.1.0-dist.zip -d bazel-1.1.0-dist
```
### 5. Grant execute permissions to some unzipped scripts
```bash
cd bazel-1.1.0-dist/src
sudo chmod 777 *.sh
cd ..
```
### 6. Use the command below in your session to expand access limits to system resources:
```bash
ulimit -c unlimited
```
### 7. Start Bazel's building with the following command:
```bash
sudo env BAZEL_JAVAC_OPTS="-J-Xms1g -J-Xmx1g" EXTRA_BAZEL_ARGS="--host_javabase=@local_jdk//:jdk --discard_analysis_cache --nokeep_state_after_build --notrack_incremental_state" bash ./compile.sh
```
The building process will take a half of hour.
### 8. Verify built Bazel binary file:
```bash
cd output
./bazel version
```
### 9. Install Bazel on your system with a simple command:
```bash
sudo cp bazel /usr/bin
```
### Hey! Now you have the latest version of Bazel installed on your system! Imagine the possibilities!
