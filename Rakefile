require 'fileutils'

task(:default).clear
task default: :new

desc 'build'
task :build do
  sh 'bundle exec jekyll build'
end

desc 'install gems by bundler'
task :install do 
  sh 'bundle install --path vendor/bundle'
end

desc 'create new post'
task :new do
  DATE = Time.now
  PATH = "_posts/#{DATE.strftime '%Y/%m/%d'}"
  FILE = "#{DATE.strftime '%F'}-%02d.md"

  path = sprintf("#{PATH}/#{FILE}", Dir.glob("#{PATH}/*.md").length + 1)
  text = <<-'EOB'.gsub(/^\s+\|/, '')
    |---
    |layout: post
    |title:
    |---
  EOB

  FileUtils.makedirs(File.dirname path)
  File.write(path, text)

  sh "$EDITOR #{path}"
end

desc 'preview in local'
task :preview do
  sh 'bundle exec jekyll serve --watch'
end
