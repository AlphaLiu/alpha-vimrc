desc 'deploy vimrc'
task :deploy  do
	puts "********** Installing vim plugins **********"
	home_dir = ENV['HOME'] 
	vimrc_file = "#{home_dir}/.vimrc"
	vimrc_bak_file = "#{home_dir}/vimrc_old"
	ackrc_file = "#{home_dir}/.ackrc"
	vundle_dir = "#{home_dir}/.vim/bundle/vundle"

	if File.exist?("#{vimrc_file}")
		puts "********** Backup the exist .vimrc to $VIMRC_BAK  **********"		
		FileUtils.mv "#{vimrc_file}", "#{vimrc_bak_file}"
	end


	unless File.exist?("#{ackrc_file}")
		system "curl -L https://raw.github.com/SaitoWu/dotfiles/master/ackrc > ~/.ackrc"
	end

	FileUtils.cp "vimrc_install", "#{vimrc_file}"

	unless Dir.exist?(vundle_dir)
		system "git clone https://github.com/gmarik/vundle.git $HOME/.vim/bundle/vundle"	
	end

	system "vim +BundleInstall +qall"

	system "cat vimrc >> #{vimrc_file}"

	puts "********** Installation Done! **********"
	puts "* Notes: ack.vim requires \"ack\" in your system, please read the documentations in http://betterthangrep.com/"
end

desc 'update plugins'
task :update do
	system "vim +BundleInstall! +qall"
end
