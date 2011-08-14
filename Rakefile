namespace :deploy do
  task :ensure_tmp_exists do
    unless File.exists?(File.expand_path(File.join(File.dirname(__FILE__), 'tmp')))
      puts "creating tmp/ directory for passenger restart file..."
      Dir.mkdir(File.expand_path(File.join(File.dirname(__FILE__), 'tmp')))
    end
  end
	
  task :restart_passenger do
    puts "restarting Passenger web server"
    Dir.chdir(File.expand_path(File.join(File.dirname(__FILE__), 'tmp')))
    system("touch restart.txt")
  end

  task :post_setup => [ :ensure_tmp_exists ]
  task :post_deploy => [ :ensure_tmp_exists, :restart_passenger ]
end

