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
  count = 1
  today = Time.now

  path = "_posts/#{today.strftime '%Y/%m/%d'}"
  file = "#{path}/#{today.strftime '%F'}-%02d.md"

  while File.exist?(file % count) do
    count += 1
  end

  template = <<-'EOB'.gsub(/^\s+\|/, '')
    |---
    |layout: post
    |title:
    |---
  EOB

  FileUtils.makedirs(path)
  File.write(file % count, template)

  sh "$EDITOR #{file % count}"
end

desc 'preview in local'
task :preview do
  sh 'bundle exec jekyll serve --watch'
end
