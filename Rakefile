#rake task to generate file list until we version on each master commit
require 'rubygems'
require 'json'

desc "One line task description"
task :generate_policy_list do
  file_list = []
  Dir['**/*.pt'].each do |file|
    f = File.read(file)
    f.each_line do |line|
      if line =~ /long_description/
        if line =~ /Version/
          version = line.split(':').last.strip.chomp("\"")
          file_list<<{"name": file, "version": version }
        end
      end
    end
  end
  policies = {"policies": file_list }
  File.open('active-policy-list.json', 'w') { |file| file.write(policies.to_json) }
end
