# MemGuard-X

A DRAM memory controller in SystemVerilog with a bank-aware
scheduler (FCFS and FR-FCFS) and SECDED ECC.

## Planned blocks
- Request interface (valid/ready)
- Sync FIFO
- Address decoder (bank group / bank / row / column)
- Bank state tracker (open row per bank)
- Scheduler: FCFS and FR-FCFS
- Arbiter
- SECDED ECC
- Verification environment (scoreboard, random tests, coverage)

## Progress log
- Day 1: repo created, DRAM notes added
