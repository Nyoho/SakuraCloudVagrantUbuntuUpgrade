Vagrant.configure("2") do |config|
  config.vm.box = "dummy"
  config.ssh.username = "ubuntu"
  config.ssh.private_key_path = File.expand_path "~/.ssh/id_dsa"

  config.vm.define "My Ubuntu Server"

  config.vm.provider :sakura do |sakura|
    sakura.access_token = ENV['ACCESS_TOKEN']
    sakura.access_token_secret = ENV['ACCESS_TOKEN_SECRET']
    sakura.disk_plan = "4"
    sakura.disk_source_archive = "112500459149"
    sakura.server_name = "UbuntuServer"
    sakura.sshkey_id = ENV['SSHKEY_ID']
    sakura.zone_id = "is1a"
  end
end
