require 'rake'

template_files = Rake::FileList["Hermes/templates/**/*.docx"]

task :default => :docx
task :docx => template_files

rule ".docx" => ".adoc" do |t|
  file_in = t.name
  file_out = t.source.gsub(/Hermes\//, '')
  dir_out = File.dirname(file_out)
  FileUtils.mkdir_p dir_out
  extract_media_dir = dir_out + "/media"

  sh "pandoc \
           --from=docx \
           --to=asciidoc \
           --wrap=none \
           --atx-headers \
           --normalize \
           --extract-media=#{extract_media_dir} \
     '#{file_in}' > '#{file_out}'"
end
