task :default do
  dir = File.dirname(__FILE__)
  results = `#{ File.join(dir, 'bin', 'mdl') } #{ File.join(dir, '.') }`

  if results.strip.length > 0
    puts results
    exit 1
  end

  exit 0
end
