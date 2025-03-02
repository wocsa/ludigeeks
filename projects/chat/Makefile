# Define required versions for Node.js, Yarn, and Git
NODE_VERSION_REQUIRED := 22.0.0
YARN_VERSION_REQUIRED := 1.22.0
GIT_VERSION_REQUIRED := 2.30.0

# Define repositories and branches
REPO_URL_BASE := https://github.com/Beetix/
REPO_EXTENSION := .git
REPO_BRANCH := mqtt_extension

# Define project directories
DIR_L10N := scratch-l10n
DIR_VM := scratch-vm
DIR_GUI := scratch-gui
VENV_DIR := .venv_node  # Virtual environment directory

# Define all targets as PHONY to prevent conflicts with files
.PHONY: install check-env install-venv install-node install-yarn install-git check-dirs check-l10n check-vm check-gui run clean

# -------------------------------------------------------------------
# 📌 Default target: Install Everything
# Sets up the virtual environment, installs Node.js, Yarn, Git,
# clones repositories, installs dependencies, and sets up links.
# -------------------------------------------------------------------
install: check-env check-dirs
	@echo "✅ Installation complete!"

# -------------------------------------------------------------------
# Ensure required tools (Node.js, Yarn, Git) are installed
# -------------------------------------------------------------------
check-env: install-venv install-node install-yarn install-git
	@echo "✅ Environment setup completed!"

# -------------------------------------------------------------------
# Create a virtual environment for Node.js & Yarn if missing
# -------------------------------------------------------------------
install-venv:
	@echo "📌 Setting up virtual environment in $(VENV_DIR)..."
	@if [ ! -d "$(VENV_DIR)" ]; then \
		mkdir -p $(VENV_DIR) || { echo "❌ Failed to create $(VENV_DIR)."; exit 1; }; \
		echo "🌍 Downloading and installing NVM..."; \
		curl -fsSL https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash || { echo "❌ Failed to install NVM."; exit 1; }; \
	else \
		echo "✅ Virtual environment already exists."; \
	fi

# -------------------------------------------------------------------
# Install Node.js inside the virtual environment if missing
# -------------------------------------------------------------------
install-node: install-venv
	@echo "📌 Checking Node.js installation..."
	@if [ ! -d "$(VENV_DIR)/nvm/versions/node/$(NODE_VERSION_REQUIRED)" ]; then \
		echo "⬇️ Installing Node.js $(NODE_VERSION_REQUIRED)..."; \
		$(MAKE) _install-node; \
	else \
		echo "✅ Node.js $(NODE_VERSION_REQUIRED) already installed."; \
	fi

_install-node:
	( \
		export NVM_DIR="$(PWD)/$(VENV_DIR)/nvm"; \
		mkdir -p "$$NVM_DIR"; \
		curl -fsSL https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash; \
		[ -s "$$NVM_DIR/nvm.sh" ] && . "$$NVM_DIR/nvm.sh"; \
		nvm install $(NODE_VERSION_REQUIRED); \
		nvm use $(NODE_VERSION_REQUIRED); \
		nvm alias default $(NODE_VERSION_REQUIRED); \
		echo "✅ Node.js installed: $$(node -v)"; \
	)

# -------------------------------------------------------------------
# Install Yarn if missing
# -------------------------------------------------------------------
install-yarn: install-node
	@echo "📌 Checking Yarn installation..."
	@if ! command -v yarn &> /dev/null || [ "$(shell yarn --version 2>/dev/null)" != "$(YARN_VERSION_REQUIRED)" ]; then \
		echo "⬇️ Installing Yarn $(YARN_VERSION_REQUIRED)..."; \
		$(MAKE) _install-yarn; \
	else \
		echo "✅ Yarn $(YARN_VERSION_REQUIRED) already installed."; \
	fi

_install-yarn:
	( \
		export NVM_DIR="$(PWD)/$(VENV_DIR)/nvm"; \
		[ -s "$$NVM_DIR/nvm.sh" ] && . "$$NVM_DIR/nvm.sh"; \
		npm install -g yarn@$(YARN_VERSION_REQUIRED); \
		echo "✅ Yarn installed: $$(yarn -v)"; \
	)

# -------------------------------------------------------------------
# Install Git if missing
# -------------------------------------------------------------------
install-git:
	@echo "📌 Checking Git installation..."
	@if command -v git &> /dev/null; then \
		echo "✅ Git is already installed: $$(git --version)"; \
	else \
		echo "⬇️ Installing Git..."; \
		if command -v apt &> /dev/null; then \
			sudo apt update && sudo apt install -y git || { echo "❌ Failed to install Git."; exit 1; }; \
		elif command -v yum &> /dev/null; then \
			sudo yum install -y git || { echo "❌ Failed to install Git."; exit 1; }; \
		elif command -v brew &> /dev/null; then \
			brew install git || { echo "❌ Failed to install Git."; exit 1; }; \
		else \
			echo "❌ No supported package manager found. Install Git manually."; \
			exit 1; \
		fi; \
	fi

# -------------------------------------------------------------------
# Clone and install dependencies for all repositories if missing
# -------------------------------------------------------------------
check-dirs: check-l10n check-vm check-gui

check-l10n:
	@if [ ! -d "$(DIR_L10N)" ]; then \
		echo "⬇️ Cloning $(DIR_L10N)..."; \
		git clone --depth 1 --branch $(REPO_BRANCH) --single-branch $(REPO_URL_BASE)$(DIR_L10N)$(REPO_EXTENSION) $(DIR_L10N); \
		echo "📦 Installing and building $(DIR_L10N)..."; \
		( \
			export NVM_DIR="$(PWD)/$(VENV_DIR)/nvm"; \
			. "$$NVM_DIR/nvm.sh"; \
			cd $(DIR_L10N) && yarn install && yarn build && yarn link; \
		); \
	else \
		echo "✅ $(DIR_L10N) already exists."; \
	fi

check-vm: check-l10n
	@if [ ! -d "$(DIR_VM)" ]; then \
		echo "⬇️ Cloning $(DIR_VM)..."; \
		git clone --depth 1 --branch $(REPO_BRANCH) --single-branch $(REPO_URL_BASE)$(DIR_VM)$(REPO_EXTENSION) $(DIR_VM); \
		echo "📦 Installing and linking $(DIR_VM)..."; \
		( \
			export NVM_DIR="$(PWD)/$(VENV_DIR)/nvm"; \
			. "$$NVM_DIR/nvm.sh"; \
			cd $(DIR_VM) && yarn link scratch-l10n && yarn install && yarn link; \
		); \
	else \
		echo "✅ $(DIR_VM) already exists."; \
	fi

check-gui: check-vm
	@if [ ! -d "$(DIR_GUI)" ]; then \
		echo "⬇️ Cloning $(DIR_GUI)..."; \
		git clone --depth 1 --branch $(REPO_BRANCH) --single-branch $(REPO_URL_BASE)$(DIR_GUI)$(REPO_EXTENSION) $(DIR_GUI); \
		echo "📦 Installing and linking $(DIR_GUI)..."; \
		( \
			export NVM_DIR="$(PWD)/$(VENV_DIR)/nvm"; \
			. "$$NVM_DIR/nvm.sh"; \
			cd $(DIR_GUI) && yarn link scratch-l10n && yarn link scratch-vm && yarn install; \
		); \
	else \
		echo "✅ $(DIR_GUI) already exists."; \
	fi

# -------------------------------------------------------------------
# Run the Scratch GUI
# Ensures environment & dependencies are ready before starting
# -------------------------------------------------------------------
run: check-env check-dirs
	@echo "🚀 Starting Scratch GUI..."
	( \
		export NVM_DIR="$(PWD)/$(VENV_DIR)/nvm"; \
		. "$$NVM_DIR/nvm.sh"; \
		cd $(DIR_GUI) && yarn start; \
	)

# -------------------------------------------------------------------
# Clean up installed dependencies and virtual environment
# -------------------------------------------------------------------
clean:
	@echo "🧹 Cleaning up..."
	rm -rf $(VENV_DIR) node_modules $(DIR_L10N) $(DIR_VM) $(DIR_GUI)
	@echo "✅ Cleanup complete!"
