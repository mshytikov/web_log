##!/usr/bin/env rake

namespace :download do
  desc "Download clj-stream-sh"
  task "clj-stream-sh" do
    sh %{wget -N  -O ./app/clj-stream-sh.jar http://dl.dropbox.com/u/27498455/clj-stream-sh-0.0.1-SNAPSHOT-standalone.jar} 
  end
end


namespace :nginx do
  namespace :conf do
    desc "rake nginx:create:conf log_dir=/you_app/log  .Create config for your  log dir"
    task :create do
      log_dir =  ENV['log_dir']
      conf_file = "config/web_log.conf"
      conf = File.read(conf_file)
      conf.sub!(/(set\s+\$log_dir).*$/, "set $log_dir #{log_dir}")
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

namespace :foreman do
  desc "Export the Procfile to Ubuntu's upstart scripts"
  task :export do
    sh %{rvmsudo bundle exec foreman export upstart /etc/init -a web_log -c app=1 -u $(whoami)}
  end
end

desc "rake install log_dir=/var/log Install all on your server rake"
task :install => ["download:clj-stream-sh", "nginx:conf:create", "nginx:conf:update", "foreman:export", "nginx:reload"]
