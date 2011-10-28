# encoding: utf-8

require 'rubygems'
require 'bundler'
begin
  Bundler.setup(:default, :development)
rescue Bundler::BundlerError => e
  $stderr.puts e.message
  $stderr.puts "Run `bundle install` to install missing gems"
  exit e.status_code
end
require 'rake'

require 'jeweler'
Jeweler::Tasks.new do |gem|
  # gem is a Gem::Specification... see http://docs.rubygems.org/read/chapter/20 for more options
  gem.name = "git_pivotal_tracker_x"
  gem.homepage = "http://github.com/phuibonhoa/git_pivotal_tracker"
  gem.license = "MIT"
  gem.summary = "A git workflow integrated with Pivotal Tracker"
  gem.description = "Provides a set of git workflow tools to start and finish Pivotal Tracker stories in topic branches"
  gem.email = "phuibonhoa@gmail.com"
  gem.authors = ["Philippe Huibonhoa"]
end
Jeweler::RubygemsDotOrgTasks.new


require 'rspec/core/rake_task'
RSpec::Core::RakeTask.new(:spec)

require 'cucumber/rake/task'
Cucumber::Rake::Task.new(:cucumber) do |t|
  t.cucumber_opts = '--format progress'
end

require 'rcov/rcovtask'
Rcov::RcovTask.new do |test|
  test.libs << 'test'
  test.pattern = 'test/**/test_*.rb'
  test.verbose = true
  test.rcov_opts << '--exclude "gems/*"'
end

task :default => [:cucumber, :spec]

require 'rdoc/task'
Rake::RDocTask.new do |rdoc|
  version = File.exist?('VERSION') ? File.read('VERSION') : ""

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "git_pivotal_tracker_x #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end