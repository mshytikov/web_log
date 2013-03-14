##!/usr/bin/env rake

namespace :download do
  desc "Download clj-stream-sh"
  task "clj-stream-sh" do
    sh %{wget -N  -O ./app/clj-stream-sh.jar http://dl.dropbox.com/u/27498455/clj-stream-sh-0.0.1-SNAPSHOT-standalone.jar} 
  end
end


namespace :nginx do
  namespace :conf do
    desc "Create config for your  log dir"
    task :create do
     log_dir =  ARGV[1]
     conf_file = "config/web_log.conf"
     conf = File.read(conf_file)
     conf.sub(/(set \$log_dir).*$/, "\1 #{log_dir}")
     File.open(conf_file, "w"){ |f| f.write(conf) }
    end

    desc "Add link to nginx conf  web_log.conf"
    task :cp do
      sh %{ sudo cp ./config/web_log.conf /etc/nginx/conf.d/ }
    end

    desc "Remove config from nginx"
    task :rm do
      sh %{ sudo rm -f /etc/nginx/conf.d/web_log.conf }
    end

    desc "Update conf in nginx" 
    task :update => [:rm, :cp]

  end

  desc "Reloca nginx"
  task :reload do
    sh %{ sudo nginx -s reload }
  end
 
end
