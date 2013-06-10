require 'rubygems'

# use dowl to generate the schema into the schemas project
# should be checked out in parallel
task :publish do
    sh %{dowl schema/schema.ttl schema/dowl_template.erb >../schemas/odrs/index.html}
    FileUtils.cp 'schema/diagram.png','../schemas/odrs' 
    FileUtils.cp 'schema/schema.ttl','../schemas/odrs/index.ttl'
end