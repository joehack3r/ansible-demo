
Ansible Managing Windows
========================

The files in this repository/directory are from a demo given at the Austin Ansible meetup in August 2014. This demo and associated files provide a way to get started and experiment with using Ansible to manage Windows machines. The slides are available on slideshare (http://www.slideshare.net/joehack3r/austin-ansible-august-2014) and a blog post is being written (http://blog.joehack3r.com).

This demo assumes you are using Amazon Web Services (AWS) and VPC. If you are not using VPC, you can edit the createWindowsInstance.yml and remove vpc_subnet_id when launching the instance.

If you need help getting an Ansible Control machine running on AWS, there are CloudFormation templates in https://github.com/joehack3r/aws/tree/master/cloudformation/templates to help. A blog post is in the works to help explain my environment, thoughts, and practices when creating these templates.

Setup
=====

After cloning this repository, run the setup.sh script to configure your environment to run the demo examples.

    git clone https://github.com/joehack3r/ansible-demo.git
    cd ansible-demo && source ./demo-setup

Next, start a Windows instance to manage and add its **private ip** to the Ansible hosts file under the [windows] section:

    ansible-playbook createWindowsInstance.yml
    vi `echo $ANSIBLE_HOSTS`

Finally, look at the examples to see the different commands you can run:

    cat examples

If you want to pick a different username and password, edit UserData in createWindowsInstance.yml and the ansible_ssh_user/ansible_ssh_pass in group_vars/windows.yml.
