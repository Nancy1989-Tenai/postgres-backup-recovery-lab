# Create a project folder
mkdir -p ~/postgres-lab && cd ~/postgres-lab

# Initialize git
git init

# Copy your screenshots here
cp ~/step*.png .

# Create a README
cat > README.md << 'EOF'
# PostgreSQL Backup, PITR & Streaming Replication Lab

## Overview
This lab demonstrates:
1. Logical backup with `pg_dump` / `pg_restore`
2. WAL archiving and base backups
3. Point-in-Time Recovery (PITR) after simulated data loss
4. Streaming replication standby setup

## Steps Completed

### Step 1: Logical Backup
Backed up the `bootcamp` database using `pg_dump -Fc` and verified restore into `bootcamp_check`.

![Step 1](step1_logical_backup.png)

### Step 2: WAL Archiving & Base Backup
Enabled `wal_level = replica`, `archive_mode = on`, and took a compressed base backup with `pg_basebackup`.

![Step 2](step2_wal_archiving.png)

### Step 3: Point-in-Time Recovery
Deleted all rows from `students`, then recovered to the exact moment before deletion using WAL replay.

![Step 3](step3_pitr_recovery.png)

### Step 4: Streaming Standby
Created a `replicator` role and built a standby server using `pg_basebackup -R`.

![Step 4](step4_standby_setup.png)

### Step 5: Replication Health
Verified streaming replication is active with `pg_stat_replication`.

![Step 5](step5_replication_health.png)

## Environment
- OS: Ubuntu (adjust as needed)
- PostgreSQL version: (run `psql --version` and fill in)
EOF

# Commit and push
git add .
git commit -m "Completed PostgreSQL backup, PITR, and replication lab"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/postgres-backup-recovery-lab.git
git push -u origin main
