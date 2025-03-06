# Triggering-Workflows
# Triggering Workflows in Another Repository with GitHub Actions

This project demonstrates how to trigger workflows across repositories using GitHub Actions.

## Overview

The system consists of two repositories:
- **Repository A (Trigger Repository)**: Initiates the workflow with specific parameters
- **Repository B (Target Repository)**: Receives the trigger and executes the deployment

## Prerequisites

- GitHub Personal Access Token (PAT) with `repo` and `workflow` scopes
- Access to both repositories
- Admin permissions to configure GitHub Secrets

## Repository A (Triggering Repository)

### Features

- ✅ Input validation for service, version, and SHA
- ✅ Robust error handling
- ✅ Secure PAT management
- ✅ Comprehensive logging
- ✅ HTTP status verification

### Implementation Details

1. **Input Validation**
   - Validates required inputs: `target_service`, `target_version`, `target_sha`
   - Checks SHA format for validity
   - Prevents incomplete data transmission

2. **Error Handling**
   - Validates API response codes
   - Provides clear error messages
   - Fails gracefully with proper exit codes

3. **Security**
   - Uses GitHub Secrets for PAT storage
   - Implements proper API headers
   - Validates all inputs before processing

4. **Monitoring**
   - Logs API responses
   - Records deployment attempts
   - Tracks trigger status

## Repository B (Target Repository)

### Features

- ✅ Payload validation
- ✅ Specific commit checkout
- ✅ Deployment status tracking
- ✅ Comprehensive logging

### Implementation Details

1. **Code Checkout**
   - Uses `actions/checkout@v4`
   - Verifies commit existence
   - Ensures correct version deployment

2. **Payload Processing**
   - Validates all required fields
   - Processes service, version, and SHA
   - Handles deployment parameters

3. **Deployment Tracking**
   - Records deployment status
   - Logs all deployment steps
   - Provides deployment notifications

## Setup Instructions

### 1. Repository A Configuration

1. Create GitHub Secret:
   ```bash
   # Navigate to repository settings
   Settings > Secrets and variables > Actions > New repository secret
   # Name: PAT
   # Value: Your-Personal-Access-Token