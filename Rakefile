require 'yaml'
require 'httparty'

SECRETS = YAML.load_file('secrets.yml').freeze

namespace :remind do
  namespace :standup do
    desc 'Wallet standup'
    task :wallet do
      post <<~MESSAGE
        **Standup!** <@&313743122129747968>
        #{SECRETS['wallet_standup']}
      MESSAGE
    end

    desc 'Hound standup'
    task :hounds do
      post <<~MESSAGE
        **Standup!** <@&313742915216343041>
        #{SECRETS['hounds_standup']}
      MESSAGE
    end
  end

  desc 'Timesheets'
  task :timesheets do
    post <<~MESSAGE
      **Fill in your timesheets** @everyone**!**
      #{SECRETS['timesheets']}
    MESSAGE
  end

  def post(message)
    HTTParty.post(SECRETS['webhook'], body: {content: message})
  end
end
