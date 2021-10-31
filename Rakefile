require 'date'

task default: :new

desc 'Run the Jekyll server locally with rendered drafts.'
task :serve do
  sh 'bundle exec jekyll serve --drafts'
end

desc 'Publishing a draft'
task :publish do
  current_drafts = Dir.glob('./_drafts/*.md')
  puts 'Which entry to publish?'
  current_drafts.each_with_index do |draft, index|
    puts "#{index} -- #{draft}"
  end
  input = $stdin.gets.chomp.strip.to_i

  puts "publishing #{current_drafts[input]}..."
  file_name = current_drafts[input].split('/')[-1]
  pretty_name = file_name.delete_suffix('.md').split('-').map(&:capitalize).join(' ')
  current_date = DateTime.now.to_date.to_s
  draft_body = File.read(current_drafts[input])

  new_file = "./_posts/#{current_date}-#{file_name}"
  File.write(new_file, draft_body)
  File.delete(current_drafts[input])

  sh "git add #{new_file}"
  sh "git commit -m 'Post: #{pretty_name}'"
  sh 'git push'
end

desc 'Generating a new draft'
task :new do
  print 'title: '
  title = $stdin.gets.chomp.strip
  cleaned_title = title.downcase.gsub(/[[:punct:]]/, '').gsub(/\s/, '-')
  formatted_title = "./_drafts/#{cleaned_title}.md"

  File.write(formatted_title, mkheader(title))
end

def mkheader(title)
  current_date = DateTime.now
  <<~DOC
    ---
    layout: post
    author: Mordecai
    title: "#{title}"
    date: #{current_date.rfc822}
    categories: post
    ---

  DOC
end
