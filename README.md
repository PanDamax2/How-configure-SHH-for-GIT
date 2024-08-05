
# SSH configuration for Git

## Table of contents

- [Polski](#polski)
- [English](#english)

---

## Polski

Aby skonfigurować SSH dla Git na komputerze, musisz wygenerować klucze SSH i dodać klucz publiczny do swojego konta na platformie Git (np. GitHub, GitLab, Bitbucket). Oto krok po kroku, jak to zrobić:

### Krok 1: Sprawdź, czy masz zainstalowane narzędzie SSH

#### Windows

Jeśli używasz systemu Windows, zaleca się zainstalowanie **Git Bash**, który zawiera narzędzia SSH.

1. **Pobierz Git Bash**: [Git for Windows](https://gitforwindows.org/)
2. **Zainstaluj Git Bash**: Postępuj zgodnie z instrukcjami instalatora.

#### macOS i Linux

SSH jest zazwyczaj preinstalowany w systemach macOS i Linux.

### Krok 2: Generowanie klucza SSH

1. **Otwórz terminal** lub Git Bash.
    
2. **Wygeneruj klucz SSH** używając poniższej komendy:
    
    ```bash
    ssh-keygen -t ed25519 -C "twojemail@example.com"
    ```
    
    - `-t ed25519`: Specyfikuje użycie algorytmu Ed25519 (zalecany). Jeśli masz starszy system, który nie obsługuje Ed25519, możesz użyć `-t rsa`.
    - `-C "twojemail@example.com"`: Dodaje etykietę do klucza (np. Twój adres e-mail).
3. **Podaj lokalizację do zapisania klucza** (lub naciśnij Enter, aby użyć domyślnej ścieżki: `~/.ssh/id_ed25519`).
    
4. **Podaj hasło (opcjonalnie)**, aby zabezpieczyć klucz, lub pozostaw puste, aby nie używać hasła.
    

### Krok 3: Dodanie klucza publicznego do agenta SSH

1. **Uruchom agenta SSH**:
    
    ```bash
    eval "$(ssh-agent -s)"
    ```
    
2. **Dodaj klucz SSH do agenta**:
    
    ```bash
    ssh-add ~/.ssh/id_ed25519
    ```
    

### Krok 4: Skopiowanie klucza publicznego

1. **Skopiuj zawartość klucza publicznego** do schowka:
    
    ```bash
    # Dla systemów macOS/Linux:
    cat ~/.ssh/id_ed25519.pub | pbcopy
    
    # Dla Git Bash na Windows:
    cat ~/.ssh/id_ed25519.pub | clip
    ```
    

### Krok 5: Dodanie klucza SSH do konta Git

#### GitHub

1. Zaloguj się na [GitHub](https://github.com/).
2. Przejdź do **Settings** > **SSH and GPG keys**.
3. Kliknij **New SSH key**.
4. Wklej skopiowany klucz publiczny do pola **Key**.
5. Nadaj nazwę dla klucza (np. "Mój Komputer").
6. Kliknij **Add SSH key**.

#### GitLab

1. Zaloguj się na [GitLab](https://gitlab.com/).
2. Przejdź do **User Settings** > **SSH Keys**.
3. Wklej klucz publiczny w polu **Key**.
4. Nadaj nazwę dla klucza (Title).
5. Kliknij **Add key**.

#### Bitbucket

1. Zaloguj się na [Bitbucket](https://bitbucket.org/).
2. Przejdź do **Personal settings** > **SSH keys**.
3. Kliknij **Add key**.
4. Wklej klucz publiczny w polu **Key**.
5. Nadaj nazwę dla klucza (Label).
6. Kliknij **Add SSH key**.

### Krok 6: Testowanie konfiguracji SSH

1. **Przetestuj połączenie SSH** z platformą Git:
    
    ```bash
    ssh -T git@github.com
    ```
    
    Lub dla innych platform:
    
    ```bash
    ssh -T git@gitlab.com
    ssh -T git@bitbucket.org
    ```
    
2. Powinieneś zobaczyć wiadomość podobną do:
    
    ```bash
    Hi username! You've successfully authenticated, but GitHub does not provide shell access.
    ```
    

### Podsumowanie

Teraz Twój komputer powinien być skonfigurowany do używania SSH z Git. Stwórz przykładowe repozytorium i zaloguj się do githuba.

---

## English

To configure SSH for Git on your computer, you need to generate SSH keys and add the public key to your account on a Git platform (e.g., GitHub, GitLab, Bitbucket). Here is a step-by-step guide on how to do this:

### Step 1: Check if SSH is Installed

#### Windows

If you are using Windows, it is recommended to install **Git Bash**, which includes SSH tools.

1. **Download Git Bash**: [Git for Windows](https://gitforwindows.org/)
2. **Install Git Bash**: Follow the instructions of the installer.

#### macOS and Linux

SSH is typically pre-installed on macOS and Linux systems.

### Step 2: Generate an SSH Key

1. **Open a terminal** or Git Bash.
    
2. **Generate an SSH key** using the following command:
    
    ```bash
    ssh-keygen -t ed25519 -C "youremail@example.com"
    ```
    
    - `-t ed25519`: Specifies the use of the Ed25519 algorithm (recommended). If you have an older system that doesn't support Ed25519, you can use `-t rsa`.
    - `-C "youremail@example.com"`: Adds a label to the key (e.g., your email address).
3. **Specify a location to save the key** (or press Enter to use the default path: `~/.ssh/id_ed25519`).
    
4. **Enter a passphrase (optional)** to secure the key, or leave it empty to use no passphrase.
    

### Step 3: Add the Public Key to the SSH Agent

1. **Start the SSH agent**:
    
    ```bash
    eval "$(ssh-agent -s)"
    ```
    
2. **Add the SSH key to the agent**:
    
    ```bash
    ssh-add ~/.ssh/id_ed25519
    ```
    

### Step 4: Copy the Public Key

1. **Copy the contents of the public key** to the clipboard:
    
    ```bash
    # For macOS/Linux:
    cat ~/.ssh/id_ed25519.pub | pbcopy
    
    # For Git Bash on Windows:
    cat ~/.ssh/id_ed25519.pub | clip
    ```
    

### Step 5: Add the SSH Key to Your Git Account

#### GitHub

1. Log in to [GitHub](https://github.com/).
2. Go to **Settings** > **SSH and GPG keys**.
3. Click **New SSH key**.
4. Paste the copied public key into the **Key** field.
5. Give the key a title (e.g., "My Computer").
6. Click **Add SSH key**.

#### GitLab

1. Log in to [GitLab](https://gitlab.com/).
2. Go to **User Settings** > **SSH Keys**.
3. Paste the public key into the **Key** field.
4. Give the key a title (Title).
5. Click **Add key**.

#### Bitbucket

1. Log in to [Bitbucket](https://bitbucket.org/).
2. Go to **Personal settings** > **SSH keys**.
3. Click **Add key**.
4. Paste the public key into the **Key** field.
5. Give the key a label (Label).
6. Click **Add SSH key**.

### Step 6: Test Your SSH Configuration

1. **Test the SSH connection** to the Git platform:
    
    ```bash
    ssh -T git@github.com
    ```
    
    Or for other platforms:
    
    ```bash
    ssh -T git@gitlab.com
    ssh -T git@bitbucket.org
    ```
    
2. You should see a message similar to:
    
    ```bash
    Hi username! You've successfully authenticated, but GitHub does not provide shell access.
    ```
    

### Summary

Now your computer should be configured to use SSH with Git. Create a sample repository and log in to github.
