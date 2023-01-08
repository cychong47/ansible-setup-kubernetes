# Setup github-action runner

## How to use

### Step 1. Clone the project


### Step 2. Configure variables
```
$ vi ansible-vars.yaml
```

### Step 3. Configure deploy target machine 

`Settings` - `Secrets` - `Actions` - `GH_BLOG_TARGET`


### Step 4. Get a new github token

Go to `Settings` - `Actions` - `Runner` - `Create self-hosted runner` - `Configure` and get from the token from commands

For example, 
```
# Create the runner and start the configuration experience  
$ ./config.sh --url https://github.com/GH_USERNAME/GH_REPO_NAME --token <TOKEN_VALUE>

# Last step, run it!  
$ ./run.sh
```

### Step 5. Create a non-root user at target machine
```
adduser REMOTE_USERNAME
```

```
$ vi /etc/sudoers.d/<REMOTE_USERNAME>
REMOTE_USERNAME ALL=(ALL:ALL) NOPASSWD: ALL
```

### Step 6. Run an ansible playbok
```
ansible-playbook -i hosts.txt --limit action_runner setup-action-runner.yaml -v
```
