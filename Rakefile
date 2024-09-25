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


if RUBY_VERSION.start_with?("2.1") or RUBY_VERSION.start_with?("2.2") or RUBY_VERSION.start_with?("2.0")
  require 'jeweler'
  @taskClass = Jeweler
else
  require 'juwelier'
  @taskClass = Juwelier
end


#Juwelier

@taskClass::Tasks.new do |gem|
  # gem is a Gem::Specification... see http://docs.rubygems.org/read/chapter/20 for more options
  gem.name = "bio-samtools-wrapper"
  gem.homepage = "https://github.com/cb2e6f/bio-samtools-wrapper"
  gem.license = "GPL-3.0"
  gem.summary = %Q{wrapper of samtools for ruby.}
  gem.description = %Q{wrapper of samtools for ruby.

  This project was born from the need to add support of BAM files to 
  the gee_fu genome browser (http://github.com/danmaclean/gee_fu).}
  gem.email = "rob.ellis@jic.ac.uk"
  gem.authors = ["Rob Ellis"]
  # Include your dependencies below. Runtime dependencies are required when using your gem,
  # and development dependencies are only needed for development (ie running rake tasks, tests, etc)
  #  gem.add_runtime_dependency 'jabber4r', '> 0.1'
  #  gem.add_development_dependency 'rspec', '> 1.2.3'
  gem.extensions = "ext/mkrf_conf.rb"
end
@taskClass::RubygemsDotOrgTasks.new

require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.pattern = 'test/**/test_*.rb'
  test.verbose = true
end


if RUBY_VERSION.start_with?("1.8")
require 'rcov/rcovtask'
Rcov::RcovTask.new do |test|
  test.libs << 'test'
  test.pattern = 'test/**/test_*.rb'
  test.verbose = true
end
end

task :default => :test

require 'rdoc/task'
RDoc::Task.new do |rdoc|
  version = File.exist?('VERSION') ? File.read('VERSION') : ""

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "bio-samtools-wrapper #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end
