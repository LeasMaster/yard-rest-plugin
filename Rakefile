require 'rubygems'
require 'rake'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "yard-rest"
    gem.summary = %Q{A plugin for Yardoc that produces API documentation for Restful web services}
    gem.description = %Q{A plugin for Yardoc that produces API documentation for Restful web services. See README.markdown for more details}
    gem.email = 'kevin@rkn.la'
    gem.homepage = "http://github.com/rknLA/yard-rest-plugin"
    gem.authors = ['R. Kevin Nelson', 'Aisha Fenton']
    gem.add_dependency("yard", '~>0.7.4')
    gem.files = Dir.glob("{lib,example,templates/rest}/**/*.*").concat(["Rakefile"])
    gem.extra_rdoc_files = ['VERSION', 'README.markdown']
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: gem install jeweler"
end


desc "Rebuild the gem from the gemspec"
task :rebuild do
  gemfilename = 'yard-rest-' + File.open('VERSION').gets.strip + '.gem'
  `rm yard-rest-*.gem`
  `gem uninstall yard-rest&& \
   gem build yard-rest.gemspec && \
   gem install #{gemfilename}`
end

namespace :ex do
  desc "Generate example docs"
  task :generate do
    `yardoc 'example/*.rb' --backtrace -e ./lib/yard-rest.rb -r example/README.markdown --title 'Sample API'`
  end

  desc "Clean example docs"
  task :clean do
    `rm -R doc`
    `rm -R .yardoc`
  end
end
