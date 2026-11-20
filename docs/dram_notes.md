# DRAM Notes

## Structure
- Chip -> many banks -> each bank is a grid of rows x columns
- Bank = independent block of cells with its own row buffer
- Row = one line of cells; Column = picks which 8 bits
- Row buffer = holds the one open row of a bank

## Address
- Bank group (3 bits) + bank (2) + row (16) + column (10) = 31 bits
- Sent in 2 steps: (bank + row) first, then column

## Commands
- PRE: close the open row
- ACT: open a row into the row buffer
- RD/WR: read or write 8 bits using the column address
- Sequence for a miss: PRE -> ACT -> RD/WR

## Row hit vs row miss
- Hit: needed row already open -> go straight to RD/WR (fast)
- Miss: different row open -> PRE, ACT, RD/WR (slow)
- Thrashing: jumping between rows constantly (wasteful)

## Why many banks
- Each bank keeps its own row open -> more hits
- Banks work in parallel -> one can be busy while another serves requests

## Timing parameters
- PRE, ACT and reads each take a fixed number of clock cycles
- Use parameters in code, don't hardcode

## Scheduling
- FCFS: serve in arrival order
- FR-FCFS: row hits first, then oldest
- Example: row 7 open, requests for rows 4, 7, 7
  - FCFS: 4, 7, 7 -> 2 misses + 1 hit
  - FR-FCFS: 7, 7, 4 -> 2 hits + 1 miss

## Skipped for now
- Burst buffer, refresh
