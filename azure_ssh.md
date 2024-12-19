# Setting Up SSH-Based Authentication for Azure DevOps Repositories

## Prerequisites

Ensure you have the following:

1. **Azure DevOps Account**: [Sign up here](https://azure.microsoft.com/en-us/services/devops/) if you don't have one.
2. **Git Installed**: [Download Git](https://git-scm.com/downloads).
3. **SSH Client**: Ensure your system has an SSH client installed (e.g., OpenSSH).
4. **Access to CLI**: Familiarity with terminal (macOS/Linux) or PowerShell (Windows).

---

## Step 1: Generate an SSH Key Pair

### macOS/Linux

```bash
ssh-keygen -t rsa -b 4096 -f ~/.ssh/azure
```

- **`-t rsa`**: Specifies RSA key type.
- **`-b 4096`**: Sets key size to 4096 bits.
- **`-f ~/.ssh/azure`**: Saves the key as `~/.ssh/azure`.

1. Follow the prompts to set a passphrase (optional).
2. Verify the keys:

    ```bash
    ls ~/.ssh/azure*
    ```

    You should see `azure` and `azure.pub`.

### Windows

1. Open PowerShell and run:

    ```powershell
    ssh-keygen -t rsa -b 4096 -f ~/.ssh/azure
    ```

2. Follow the prompts and verify the keys:

    ```powershell
    ls ~/.ssh/azure*
    ```

---

## Step 2: Add the SSH Private Key to the SSH Agent

### macOS/Linux

1. Start the SSH agent:

    ```bash
    eval "$(ssh-agent -s)"
    ```

2. Add the private key:

    ```bash
    ssh-add ~/.ssh/azure
    ```

### Windows

1. Start the SSH agent service:

    ```powershell
    Start-Service ssh-agent
    ```

2. Add the private key:

    ```powershell
    ssh-add ~\.ssh\azure
    ```

---

## Step 3: Add the SSH Public Key to Azure DevOps

1. Copy the public key:

    - macOS/Linux:

        ```bash
        pbcopy < ~/.ssh/azure.pub
        ```

    - Windows:

        ```powershell
        Get-Content ~\.ssh\azure.pub | Set-Clipboard
        ```

2. Log in to [Azure DevOps](https://dev.azure.com/).
3. Navigate to **Profile > Security**.
4. Under **SSH Public Keys**, click **Add**.
5. Paste the public key and save.

---

## Step 4: Configure Git to Use SSH with Azure DevOps

1. Create or edit the SSH config file:

    ```bash
    nano ~/.ssh/config
    ```

2. Add the following configuration:

    ```plaintext
    Host azure-devops
        HostName ssh.dev.azure.com
        User git
        IdentityFile ~/.ssh/azure
    ```

3. Save and exit the file.

4. Test the connection:

    ```bash
    ssh -T git@ssh.dev.azure.com
    ```

    You should see: `Shell access is not supported.`

---

## Step 5: Clone Your Azure DevOps Repository Using SSH

1. Go to your repository in Azure DevOps.
2. Click **Clone** and select the SSH URL.
3. Clone the repository:

    ```bash
    git clone git@ssh.dev.azure.com:v3/Organization/Project/Repo
    ```

---

## Step 6: Configure Existing Repositories to Use SSH

1. Navigate to your repository:

    ```bash
    cd path/to/repo
    ```

2. Update the remote URL:

    ```bash
    git remote set-url origin git@ssh.dev.azure.com:v3/Organization/Project/Repo
    ```

3. Verify the update:

    ```bash
    git remote -v
    ```

---

## Step 7: Test Git Operations

1. Fetch changes:

    ```bash
    git fetch
    ```

2. Push a test commit:

    ```bash
    echo "# Test SSH Setup" >> README.md
    git add README.md
    git commit -m "Test SSH setup"
    git push origin main
    ```

---

## Additional Tips

1. **Protect Your Private Key:**
   - Never share your private key.
   - Use strong passphrases.

2. **Manage Multiple Keys:** Use the SSH config file to specify keys for different services:

    ```plaintext
    Host github
        HostName github.com
        User git
        IdentityFile ~/.ssh/github_rsa

    Host azure-devops
        HostName ssh.dev.azure.com
        User git
        IdentityFile ~/.ssh/azure
    ```

3. **Troubleshooting:**
   - Use verbose mode to debug SSH connections:

        ```bash
        ssh -v git@ssh.dev.azure.com
        ```

   - Ensure correct file permissions:

        ```bash
        chmod 700 ~/.ssh
        chmod 600 ~/.ssh/azure
        chmod 644 ~/.ssh/azure.pub
        ```

---

## Conclusion

You have successfully set up SSH-based authentication for Azure DevOps. This enhances security and streamlines Git operations by eliminating the need for repeated credential entry.
