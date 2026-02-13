# Distributed DDoS Mitigator

Distributed system for real-time DDoS mitigation using BGP flowspec and eBPF/XDP.

## Features

- **BGP Flowspec Integration**: Announce filtering rules via BGP
- **eBPF/XDP Filtering**: High-performance packet filtering at kernel level
- **Distributed Coordination**: Multiple mitigation nodes
- **Real-time Detection**: Traffic analysis and anomaly detection
- **BGP Route Server Support**: Integration with BGP speakers

## Architecture

```
distributed-ddos-mitigator/
├── core/              # Core mitigation logic
├── filter.c           # eBPF/XDP filter programs
├── xdp_prog.c         # XDP packet processing
├── mitigator.go       # Go coordination layer
├── ARCHITECTURE.md    # Detailed architecture
└── README.md          # This file
```

## Requirements

- Go 1.21+
- Linux 5.x with XDP support
- libbpf headers
- BGP speaker (optional)

## Usage

### Build

```bash
# Build Go components
go build -o mitigator mitigator.go

# Compile eBPF programs
clang -O2 -target bpf -c filter.c -o filter.o
```

### Run

```bash
# Start monitoring
./mitigator

# Load XDP program
ip link set dev eth0 xdp prog filter.o
```

## CI/CD

Automated builds and testing:
- Go build verification
- C compilation checks
- Code formatting

## Disclaimer

**Educational Use Only**: This tool is for network security learning and authorized testing only.

## License

MIT
