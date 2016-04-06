require "rubygems"
require "tmpdir"

GITHUB_REPONAME = "Liduska/liduska.github.io"

namespace :site do

  desc "Generate and publish"
  task :publish do
    Dir.mktmpdir do |tmp|
      cp_r ["images", "styles", "libs", "CNAME", "index.html"], tmp

      Dir.chdir tmp
      system "git init"
      system "git add ."
      message = "Site updated at #{Time.now.utc}"
      system "git commit -m #{message.inspect}"
      system "git remote add origin git@github.com:#{GITHUB_REPONAME}.git"
      system "git push origin master:refs/heads/master --force"
    end
  end
end
