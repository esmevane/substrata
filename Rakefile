require 'bundler/gem_tasks'
require 'rake'
require 'rake/testtask'

Rake::TestTask.new do |task|
  task.test_files = Dir.glob 'spec/**/*_spec.rb'
  task.libs.push 'spec'
end

task default: :test
