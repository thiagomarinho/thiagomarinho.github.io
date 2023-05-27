require "rubygems"
require "tmpdir"
require "bundler/setup"
require "jekyll"

# Indique o nome do seu repositório
GITHUB_REPONAME = "thiagomarinho/thiagomarinho.github.io"

desc "Geração de site estático"
task :generate do
  Jekyll::Site.new(Jekyll.configuration({
    "source"      => ".",
    "destination" => "_site"
  })).process
end

desc "Geração de site estático e publicação no GitHub"
task :publish => [:generate] do
  Dir.mktmpdir do |tmp|
    cp_r "_site/.", tmp

    pwd = Dir.pwd
    Dir.chdir tmp
    File.open(".nojekyll", "wb") { |f| f.puts("Generated locally.") }

    system "git init"  
    system "git add ."
    message = "Updated at #{Time.now.utc}"
    system "git commit -m #{message.inspect}"
    system "git remote add origin git@github.com:#{GITHUB_REPONAME}.git"
    system "git checkout -b gh-pages"
    system "git push origin gh-pages --force"

    Dir.chdir pwd
  end
end
