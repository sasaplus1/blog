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
  def getTodayPostCount(filePath)
    count = 1
    while File.exist?(sprintf(filePath, count)) do
      count += 1
    end
    count
  end

  def forceCreateFile(filePath, text)
    FileUtils.makedirs(File.dirname(filePath))
    File.write(filePath, text)
    nil
  end

  DATE = Time.now
  PATH = "_posts/#{DATE.strftime '%Y/%m/%d'}/#{DATE.strftime '%F'}-%02d.md"

  path = sprintf(PATH, getTodayPostCount(PATH))
  text = <<-'EOB'.gsub(/^\s+\|/, '')
    |---
    |layout: post
    |title:
    |---
  EOB

  forceCreateFile(path, text)

  sh "$EDITOR #{path}"
end

desc 'preview in local'
task :preview do
  sh 'bundle exec jekyll serve --watch'
end
