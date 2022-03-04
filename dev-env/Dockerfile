FROM erdnase/vm:generic

# .NET 5.0 SDK
RUN wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb && dpkg -i packages-microsoft-prod.deb && rm packages-microsoft-prod.deb && apt-get update && DEBIAN_FRONTEND="noninteractive" apt-get install -y apt-transport-https dotnet-sdk-5.0 python-is-python3
RUN echo "DOTNET_CLI_TELEMETRY_OPTOUT=1" >> /etc/environment
ENV DOTNET_CLI_TELEMETRY_OPTOUT=1

# F# IDE
USER vagrant
RUN cd /home/vagrant && aria2c -q "https://download.jetbrains.com/product?code=rd&latest&distribution=linux" && tar xf *.tar.gz && rm *.tar.gz

# clone official restler and build
USER vagrant
RUN cd /home/vagrant && git clone 'https://github.com/microsoft/restler-fuzzer.git' && mkdir restler-bin && cd restler-fuzzer/ && python ./build-restler.py --dest_dir /home/vagrant/restler-bin/

# Pycharm Professional
USER vagrant
RUN cd /home/vagrant && aria2c -q "https://download.jetbrains.com/product?code=PC&latest&distribution=linux" && tar xf *.tar.gz && rm *.tar.gz

USER root
