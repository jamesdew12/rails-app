FROM ruby:2.5
RUN apt-get update -qq && apt-get install -y nodejs postgresql-client
RUN mkdir /mock_polystream-tech-test
WORKDIR /mock_polystream-tech-test
COPY Gemfile /mock_polystream-tech-test/Gemfile
COPY Gemfile.lock /mock_polystream-tech-test/Gemfile.lock
RUN bundle install
COPY . /mock_polystream-tech-test

# Add a script to be executed every time the container starts.
COPY entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]
EXPOSE 3000

# Start the main process.
CMD ["rails", "server", "-b", "0.0.0.0"]
