source ENV['GEM_SOURCE'] || "https://rubygems.org"

def location_for(place)
  if place =~ /^((?:git[:@]|https:)[^#]*)#(.*)/
    [{ :git => $1, :branch => $2, :require => false }]
  elsif place =~ /^file:\/\/(.*)/
    ['>= 0', { :path => File.expand_path($1), :require => false }]
  else
    [place, { :require => false }]
  end
end

gem 'artifactory'
gem 'vanagon', *location_for(ENV['VANAGON_LOCATION'] || '~> 0.36')
gem 'packaging', *location_for(ENV['PACKAGING_LOCATION'] || '~> 0.109')
gem 'rake', '~> 13.0'

eval_gemfile("#{__FILE__}.local") if File.exist?("#{__FILE__}.local")
