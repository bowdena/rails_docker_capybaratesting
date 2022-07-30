# Hello world using Docker and Capybara

Unit tests using Capybara within remote dockers for management.

All the magic comes from:
https://nicolasiensen.github.io/2022-03-11-running-rails-system-tests-with-docker/

Setup the selenium environments
```bash
docker-compose run web bin/rails test:system
```
Running the test:
```bash
# Run the tests using the chrome browser
docker-compose run -e TEST_BROWSER=chrome web bin/rails test:system
# Run the tests using the firefox browser
docker-compose run -e TEST_BROWSER=firefox web bin/rails test:system
```
 
On failure,the output is put into <app>/tmp/screenshots (default by Capybara).
You can view the browsers run on:
http://localhost:7901/ (firefox)
http://localhost:7900/ (chrome)


All of the majick for configuration can be found in the following files:
- Dockerfile
- docker-compose.yml
- test/application_system_test_case.rb
- Gemfile (remove gem "webdrivers")
- test/test_helper.rb

