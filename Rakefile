require 'mail'
require 'rest-client'

task :default => [:greet]

task :greet do
  today = Time.now
  puts "Hello world! #{today.to_s}"
end

task :send_mail do
  r = RestClient.get("http://makingdevs.com", headers={})
  puts r
end
