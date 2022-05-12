require 'rake/file_list'

project.name = "XCTest"

project.class_prefix = "XCT"

bundle_id_prefix = "org.gnustep"

xctest_framework = target do |target|
  target.name = project.name
  target.type = :framework
  target.platform = :osx
  target.deployment_target = "10.11"

  target.include_files = ['XCTest/**/*.*']

  target.headers_build_phase do |phase|
    phase.public = Rake::FileList.new "XCTest/*.h"
  end

  target.all_configurations.each do |c|
    c.product_bundle_identifier = "#{bundle_id_prefix}.xctest"
  end
end

test_runner_tool = target do |target|
  target.name = "GSXCTestRunner"
  target.type = :command_line_tool
  target.platform = :osx
  target.deployment_target = "10.11"
  
  target.all_configurations.each { |c| c.product_bundle_identifier = "#{bundle_id_prefix}.gsxctestrunner"}

  target.include_files << "GSXCTestRunner.*"

  target.exclude_files << "XCTest/*.*"

  target.linked_targets = [xctest_framework]
end
