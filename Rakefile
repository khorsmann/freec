require 'rubygems'
require 'rake'

desc 'Clean up files.'
task :clean do |t|
  FileUtils.rm_rf "tmp"
  FileUtils.rm_rf "pkg"
end

spec = Gem::Specification.new do |s| 
  s.name              = "freec"
  s.version           = '0.2.6'
  s.author            = "Jan Kubr"
  s.email             = "mail@jankubr.com"
  s.homepage          = "http://github.com/jankubr/freec"
  s.platform          = Gem::Platform::RUBY
  s.summary           = "The layer between your Ruby voice app and FreeSWITCH."
  s.files             = FileList["README*",
                                 "Rakefile",
                                 "{lib,spec}/**/*"].to_a
  s.require_path      = "lib"
  s.rubyforge_project = "freec"
  s.has_rdoc          = false
  s.extra_rdoc_files  = FileList["README*"].to_a
  s.rdoc_options << '--line-numbers' << '--inline-source'
  s.add_dependency "daemons"
  s.add_development_dependency 'rspec', '> 2.0.1'
end

desc "Generate a gemspec file"
task :gemspec do
  File.open("#{spec.name}.gemspec", 'w') do |f|
    f.write spec.to_ruby
  end
end

require 'rspec/core/rake_task'

desc "Run all specs"
RSpec::Core::RakeTask.new(:spec) do |t|
  t.pattern = FileList['spec/**/*.rb']
end
