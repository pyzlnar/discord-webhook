require 'active_support/all'
require 'httparty'
require 'yaml'

SECRETS = YAML.load_file('secrets.yml').freeze

# NOTE
# To get the desire roleID type \@rolename on the chat.
# Copying the id from the role submenu does not work.

task :bday do
  post "今日は私の誕生日です！(//ω//)\nhttps://pbs.twimg.com/media/DVApdqUUQAE3k-P.jpg"
end

task :np do
  post "どういたしましてご主人様"
  # post "かしこまりました"
  # post "Hehehe\nhttps://cdn.awwni.me/tpkh.jpg"
  # post "ごめなさい、寝坊しました"
end

task :baka do
  post "bーバカ"
end

namespace :remind do
  namespace :standup do
    desc 'Wallet standup'
    task :wallet do
      post <<~MESSAGE
        **Standup!** <@&313743122129747968>
        #{SECRETS['wallet_standup']}
      MESSAGE
    end

    desc 'Travel wizards standup'
    task :wizards do
      post <<~MESSAGE
        **Standup!** <@&530424799319687179>
        #{SECRETS['wizards_standup']}
      MESSAGE
    end

    desc 'Travel core standup'
    task :core do
      post <<~MESSAGE
        **Standup!** <@&530425120502710292>
        #{SECRETS['core_standup']}
      MESSAGE
    end
  end

  desc 'Demo'
  task :demo do
    post "<@&313742915216343041> Demo!\n#{SECRETS['wizards_standup']}"
  end

  desc 'Timesheets'
  task :timesheets do
    post <<~MESSAGE
      **Fill in your timesheets** @everyone**!**
      #{SECRETS['timesheets']}
    MESSAGE
  end

  desc 'Monthly'
  task :monthly do
    exit if 1.week.ago.month == Date.today.month
    post <<~MESSAGE
      @everyone go to our monthly meeting!
      #{SECRETS['monthly']}
    MESSAGE
  end

  def post(message)
    HTTParty.post(SECRETS['webhook'], body: {content: message})
  end
end
