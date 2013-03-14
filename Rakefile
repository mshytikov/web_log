##!/usr/bin/env rake

namespace :download do
  desc "Download clj-stream-sh"
  task "clj-stream-sh" do
    sh %{wget -N -P ./app -O clj-stream-sh.jar http://dl.dropbox.com/u/27498455/clj-stream-sh-0.0.1-SNAPSHOT-standalone.jar} 
  end
end


namespace :nginx do
  namespace :conf do
    desc "Create config for your  log dir"
    task :create do


    end

    desc "Add link to nginx conf  web_log.conf"
    task :cp do
      sh %{ sudo cp ./config/web_log.conf /etc/nginx/conf.d/ }
    end

    task :rm do
      sh %{ sudo rm /etc/nginx/conf.d/web_log.conf }
    end
  end

  task :reload do
    sh %{ sudo nginx -s reload }
  end
 
end
