# HowTo Guide - balcony.environment.localhost

This guide provides detailed instructions for using the balcony.environment.localhost component to manage your local development system using AdministrationAsCode practices.

## Table of Contents
- [Introduction](#introduction)
- [Development Environment Setup](#development-environment-setup)
- [Basic Operations](#basic-operations)
- [Package Management Workflows](#package-management-workflows)
- [Learning Path](#learning-path)
- [Best Practices](#best-practices)
- [Troubleshooting](#troubleshooting)

## Introduction

The `balcony.environment.localhost` component provides simple Ansible playbooks that can be executed directly on your local system (localhost). This component is perfect for:

- **Learning AdministrationAsCode**: Start with local operations before managing remote systems
- **Development Environment Management**: Keep your development system updated and maintained
- **Ansible Practice**: Learn Ansible syntax and concepts in a safe environment
- **No Complexity**: No inventory files, SSH keys, or remote access required

### Key Benefits
- ✅ **No Inventory Required**: All operations target localhost directly
- ✅ **Immediate Feedback**: See results instantly on your local system
- ✅ **Safe Learning**: Practice without risk to remote systems
- ✅ **Real-World Skills**: Learn actual system administration tasks

## Development Environment Setup

### Prerequisites Check
Before starting, ensure you have the proper development environment:

1. **VS Code Extensions**: Press `Ctrl-Shift-X` to verify installed extensions
   - ✅ **Ansible Extension**: Syntax highlighting and IntelliSense
   - ✅ **YAML Extension**: YAML syntax support and validation
   - ✅ **PowerShell Extension**: PowerShell scripting support
   - ✅ **GitHub Copilot**: AI-assisted coding (if available)

2. **Terminal Access**: Use VS Code's integrated terminal for best experience

3. **Directory Setup**: Navigate to the balcony.environment.localhost directory
   ```bash
   cd /path/to/balcony.environment.localhost
   ```

### VS Code Integration
This component works perfectly with the balcony.core.code development environment:

- **Integrated Terminal**: Run playbooks directly in VS Code terminal
- **Syntax Highlighting**: Ansible and YAML syntax support
- **IntelliSense**: Auto-completion for Ansible modules and YAML
- **Git Integration**: Track changes to your playbooks
- **VS Code Tasks**: Pre-configured tasks for easy playbook execution

#### Using VS Code Tasks
VS Code tasks are pre-configured for all playbooks mentioned in this guide. To access them:

1. **Command Palette Method**: 
   - Press `Ctrl+Shift+P` (Linux/Windows) or `Cmd+Shift+P` (Mac)
   - Type "Tasks: Run Task"
   - Select from the available Ansible tasks

2. **Terminal Menu Method**:
   - Go to `Terminal > Run Task...`
   - Choose from the pre-configured playbook tasks

3. **Keyboard Shortcut**:
   - Press `Ctrl+Shift+P` and type "task" to quickly access task runner

#### Available VS Code Tasks

**Individual Playbook Tasks:**
- ✅ **Ansible: Test Connectivity (ping)** - Quick connectivity test
- ✅ **Ansible: Get Package Information** - System package inventory
- ✅ **Ansible: Update Package Cache (requires sudo)** - Update package database
- ✅ **Ansible: Check Upgradable Packages** - Find available updates
- ✅ **Ansible: Apply Package Updates (requires sudo)** - Install package updates
- ✅ **Ansible: Apply Package Updates (verbose, requires sudo)** - Install updates with detailed output


#### Task Benefits
- **No Command Memorization**: All commands pre-configured and ready to use
- **Consistent Execution**: Standardized parameters and options
- **Integrated Output**: Results appear directly in VS Code terminal
- **Error Highlighting**: VS Code can highlight and navigate to errors
- **Workflow Automation**: Complex multi-step procedures automated


### 1. System Connectivity Test
Start with testing basic Ansible connectivity to your localhost:

```bash
ansible-playbook playbook.environment.localhost.ping.yaml
```

**What this does:**
- Verifies Ansible can connect to localhost
- Tests basic Ansible functionality
- Confirms your environment is ready for automation

**Expected Output:**
```
PLAY [localhost] *************************************************

TASK [ping] *****************************************************
ok: [localhost]

PLAY RECAP ******************************************************
localhost                  : ok=1    changed=0    unreachable=0    failed=0
```

### 2. Package Information Gathering
Get detailed information about packages on your system:

```bash
ansible-playbook playbook.environment.localhost.get.packages.yaml
```

**What this does:**
- Lists all installed packages on your system
- Shows package versions and status
- Provides package inventory for your localhost

**Use Cases:**
- System audit and inventory
- Understanding what's installed on your system
- Baseline documentation for your development environment

### 3. Package Cache Update
Update your system's package cache (requires administrative privileges):

```bash
ansible-playbook playbook.environment.localhost.update.packages.cache.yaml -K
```

**Important Notes:**
- The `-K` flag prompts for your sudo password
- This is equivalent to `apt update` (Ubuntu/Debian) or `yum check-update` (RHEL/CentOS)
- Should be run before checking for upgrades or installing packages

**What this does:**
- Refreshes the local package database
- Downloads latest package information from repositories
- Prepares system for package operations

### 4. Check Upgradable Packages
Identify packages that have available updates:

```bash
ansible-playbook playbook.environment.localhost.upgradable.packages.yaml
```

**What this does:**
- Scans for packages with available updates
- Lists packages that can be upgraded
- Shows current vs. available versions

**Output Information:**
- Package names with available updates
- Current installed versions
- Available update versions
- Security update notifications (if applicable)

### 5. Apply Package Updates
Update packages on your system (requires administrative privileges):

```bash
ansible-playbook playbook.environment.localhost.update.packages.yaml -K
```

**Important Considerations:**
- The `-K` flag prompts for your sudo password
- This will actually modify your system by updating packages
- Review upgradable packages first to understand what will change
- Consider creating a system backup before major updates

