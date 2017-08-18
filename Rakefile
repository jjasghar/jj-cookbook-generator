# encoding: utf-8
# frozen_string_literal: true

require 'rubygems'
require 'English'
require 'bundler/setup'
require 'rubocop/rake_task'
require 'foodcritic'

RuboCop::RakeTask.new

FoodCritic::Rake::LintTask.new do |f|
  f.options = { fail_tags: %w(any),
                cookbook_paths: %w(cookbooks/code_generator) }
end

begin
  require 'github_changelog_generator/task'

  GitHubChangelogGenerator::RakeTask.new :changelog do |config|
    config.future_release = '1.0.0'
    config.issues = true
  end
rescue LoadError
  puts 'github_changelog_generator is not available. gem install github_changelog_generator to generate changelogs'
end


task default: %w(rubocop foodcritic)
