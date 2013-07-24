Vagrant.configure("2") do |config|
  config.vm.box = "dummy"

  config.omnibus.chef_version = :latest

  config.vm.provision :chef_solo do |chef|
    chef.run_list = [
      "recipe[nginx]"
    ]
  end

  config.vm.provider :aws do |aws, override|
    aws.access_key_id     = ENV['AWS_ACCESS_KEY_ID']
    aws.secret_access_key = ENV['AWS_SECRET_ACCESS_KEY']
    aws.keypair_name = "artsnet"
    aws.instance_type = "t1.micro"
    aws.region = "ap-northeast-1"
    aws.ami = "ami-25c25424"
    aws.security_groups = ['artsnet']
    aws.tags = {
      'Name' => 'vagrant-test',
      'Description' => 'vagrant test'
    }
    override.ssh.username = "ec2-user"
    override.ssh.private_key_path = "/Users/ufuru/.ssh/artsnet.pem"
  end
end
