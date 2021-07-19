require 'active_support/core_ext/string'
# Defines the matching rules for Guard.
guard :minitest, spring: "bin/rails test", all_on_start: false do
watch(%r{^test/(.*)/?(.*)_test\.rb$}) watch('test/test_helper.rb') { 'test' } watch('config/routes.rb') { interface_tests } watch(%r{app/views/layouts/*}) { interface_tests } watch(%r{^app/models/(.*?)\.rb$}) do |matches|
["test/models/#{matches[1]}_test.rb", "test/integration/microposts_interface_test.rb"]
end
watch(%r{^test/fixtures/(.*?)\.yml$}) do |matches|
"test/models/#{matches[1].singularize}_test.rb" end
watch(%r{^app/mailers/(.*?)\.rb$}) do |matches| "test/mailers/#{matches[1]}_test.rb"
end
watch(%r{^app/views/(.*)_mailer/.*$}) do |matches|
"test/mailers/#{matches[1]}_mailer_test.rb" end
watch(%r{^app/controllers/(.*?)_controller\.rb$}) do |matches| resource_tests(matches[1])
end
watch(%r{^app/views/([^/]*?)/.*\.html\.erb$}) do |matches|
["test/controllers/#{matches[1]}_controller_test.rb"] +
    integration_tests(matches[1])
  end
watch(%r{^app/helpers/(.*?)_helper\.rb$}) do |matches| integration_tests(matches[1])
end