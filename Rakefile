require 'date'

task :default => :serve

task :serve do
  sh 'bundle exec jekyll serve --drafts'
end

task :new do
  current_date = DateTime.now
  print 'title: '
  title = STDIN.gets.chomp.strip
  pretty_title = title.split(/\W/).map(&:capitalize).join(" ")
  cleaned_title = title.downcase.gsub(/[[:punct:]]/, '').gsub(/\s/, '-')
  formatted_title = "./_posts/#{current_date.to_date.to_s}-#{cleaned_title}.md"

  body = <<DOC
---
layout: post
author: Mordecai
title: "#{pretty_title}"
date: #{current_date.rfc822}
categories: notebook
---

DOC
  File.write(formatted_title, body)
end
