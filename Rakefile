require 'rest-client'
require 'json'

task :default => [:all]

task :all => [:greet, :send_mail] do
  puts "All is done"
end

task :greet do
  today = Time.now
  puts "Hello world! #{today.to_s}"
end

task :send_mail do
  token = ENV["POSTMARK_TOKEN"]
  mail_recipients = ENV["MAIL_RECIPIENTS"]
  template_id = ENV["TEMPLATE_ID"]
  headers = {
    "Accept" => "application/json",
    "X-Postmark-Server-Token" => token
  }
  payload = {
    "From" => 'info@makingdevs.com',
    "To" => mail_recipients,
    "TemplateId"  => template_id,
    "TemplateModel" => {
      "user_name" => 'John Smith'
    }
  }
  url = "https://api.postmarkapp.com/email/withTemplate"
  begin
    response = RestClient.post(url, payload.to_json, headers)
    parsed_response = JSON.parse(response)
    puts parsed_response
  rescue  RestClient::ExceptionWithResponse => e
    puts e.response.to_s
  end
end
