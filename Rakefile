$:.unshift("/Library/RubyMotion/lib")
require 'motion/project'

Motion::Project::App.setup do |app|
  # Use `rake config' to see complete project settings.
  app.name = 'MotionData'

  Dir.glob(File.join(File.dirname(__FILE__), 'lib/*.rb')).each do |file|
    app.files.unshift(file)
  end

  app.frameworks += %w{ CoreData }

  app.vendor_project(File.expand_path(File.join(File.dirname(__FILE__), '../vendor/motion_data/ext')), :static)
  app.vendor_project('vendor/motion_data/ext', :static)
end

task 'spec' do
  # This addition to the 'spec' task will close the simulator after tests run
  # if there are no errors
  sh "osascript -e 'tell application \"iphone simulator\" to quit'"
end

namespace :spec do
  desc "Auto-run specs"
  task :kick do
    sh "bundle exec kicker -c"
  end
end
