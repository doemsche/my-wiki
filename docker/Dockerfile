FROM ruby
RUN apt-get -y update && apt-get -y install libicu-dev
RUN gem install gollum
RUN gem install github-markdown org-ruby 
RUN git config --global user.email 'dos@tweaklab.org'
RUN git config --global user.name 'Dominik Schlaepfer'
VOLUME /wiki
WORKDIR /wiki
CMD ["gollum", "--port", "80", "--allow-uploads", "page","--css"]
EXPOSE 80
