# IP Port Scanner

A powerful and user-friendly web-based IP port scanner built with Streamlit. This tool allows you to scan single IPs, IP ranges, or multiple IP addresses to identify open ports and their associated services.

## 🚀 Features

### Core Functionality
- **Multi-target Scanning**: Scan single IPs, IP ranges, or multiple IP addresses
- **Flexible Port Options**: Choose from common ports, specify port ranges, or enter custom ports
- **Service Detection**: Automatically identifies common services running on open ports
- **Real-time Progress**: Live progress bars and status updates during scanning
- **Scan History**: Persistent storage and viewing of previous scan results
- **Export Capabilities**: Save scan results in JSON format

### Scanning Options
- **Single IP**: Scan a specific IP address
- **IP Range**: Scan a continuous range of IP addresses (e.g., 192.168.1.1-192.168.1.50)
- **Multiple IPs**: Scan a custom list of IP addresses

### Port Selection Methods
- **Common Ports**: Pre-selected list of commonly used ports
- **Port Range**: Specify a range of ports to scan (1-65535)
- **Specific Ports**: Enter custom comma-separated port numbers

## 📋 Requirements

- Python 3.7+
- Streamlit
- Pandas
- Standard Python libraries (socket, ipaddress, json, os, datetime, time)

## 🛠️ Installation

1. **Clone or download the project**:
   ```bash
   git clone <repository-url>
   cd IpConnection
   ```

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the application**:
   ```bash
   streamlit run app.py
   ```

4. **Access the web interface**:
   Open your browser and navigate to `http://localhost:8501`

## 🎯 Usage Guide

### Basic Scanning

1. **Select Scan Type**:
   - **Single IP**: Enter one IP address (e.g., `192.168.1.1`)
   - **IP Range**: Specify start and end IPs (e.g., `192.168.1.1` to `192.168.1.10`)
   - **Multiple IPs**: Enter multiple IPs, one per line

2. **Choose Port Selection**:
   - **Common Ports**: Select from pre-defined common ports
   - **Port Range**: Specify a range (e.g., 1-1000)
   - **Specific Ports**: Enter custom ports (e.g., `80, 443, 22, 3389`)

3. **Configure Timeout**:
   - Adjust the connection timeout (0.1-5.0 seconds)
   - Lower values = faster scans, higher chance of missing slow services
   - Higher values = more accurate, slower scans

4. **Start Scan**:
   - Click "Start Scan" to begin the port scanning process
   - Monitor real-time progress and status updates

### Understanding Results

#### Table View
- **IP Address**: Target IP that was scanned
- **Port**: Port number that was found open
- **Service**: Identified service running on the port
- **Status**: Port status (Open/Closed)

#### Raw Data View
- Complete JSON output with all scan details
- Includes metadata like timestamp, scan configuration, and detailed results

### Scan History
- All previous scans are automatically saved
- View historical scan results
- Export scan data for further analysis

## 🔧 Configuration Options

### Timeout Settings
- **0.1-1.0 seconds**: Fast scanning, may miss slower services
- **1.0-3.0 seconds**: Balanced approach (recommended)
- **3.0-5.0 seconds**: Thorough scanning, slower but more accurate

### Common Ports Included
The application includes detection for these common services:

| Port | Service | Description |
|------|---------|-------------|
| 20 | FTP-data | File Transfer Protocol (Data) |
| 21 | FTP | File Transfer Protocol |
| 22 | SSH | Secure Shell |
| 23 | Telnet | Telnet Protocol |
| 25 | SMTP | Simple Mail Transfer Protocol |
| 53 | DNS | Domain Name System |
| 80 | HTTP | HyperText Transfer Protocol |
| 110 | POP3 | Post Office Protocol v3 |
| 143 | IMAP | Internet Message Access Protocol |
| 443 | HTTPS | HTTP Secure |
| 465 | SMTPS | SMTP Secure |
| 587 | SMTP | SMTP (submission) |
| 993 | IMAPS | IMAP Secure |
| 995 | POP3S | POP3 Secure |
| 3306 | MySQL | MySQL Database |
| 3389 | RDP | Remote Desktop Protocol |
| 5432 | PostgreSQL | PostgreSQL Database |
| 8080 | HTTP Alternate | Alternative HTTP port |
| 8443 | HTTPS Alternate | Alternative HTTPS port |

## 📂 File Structure

```
IpConnection/
├── app.py              # Main application file
├── requirements.txt    # Python dependencies
├── scan_history.json   # Automatically generated scan history
└── README.md          # This documentation file
```

## 🔍 Technical Details

### Core Functions

#### `check_port(ip, port, timeout=1)`
- Tests if a specific port is open on a given IP address
- Uses TCP socket connection to determine port status
- Returns `True` if port is open, `False` if closed

#### `scan_ip(ip, ports, progress_bar=None, timeout=1)`
- Scans multiple ports on a single IP address
- Updates progress bar during scanning
- Returns list of open ports with service information

#### `get_service_name(port)`
- Maps port numbers to common service names
- Returns "Unknown" for ports not in the common ports dictionary

### Data Storage
- Scan history is automatically saved to `scan_history.json`
- Results include timestamp, scan configuration, and detailed findings
- Session state maintains scan history during active sessions

### Security Considerations
- Tool performs standard TCP port scanning
- Does not attempt to exploit or penetrate systems
- Scanning should only be performed on networks you own or have permission to test
- Be aware of network policies and legal requirements in your jurisdiction

## ⚠️ Important Notes

### Legal and Ethical Use
- **Only scan networks you own or have explicit permission to test**
- Unauthorized port scanning may violate terms of service or local laws
- This tool is intended for network administration and security testing purposes
- Always follow responsible disclosure practices

### Performance Considerations
- Scanning large IP ranges or port ranges can take significant time
- Network latency affects scan duration
- Consider using appropriate timeout values based on your network environment
- Large scans may generate significant network traffic

### Limitations
- TCP port scanning only (no UDP support)
- Basic service detection (name mapping only)
- No advanced fingerprinting or vulnerability detection
- Requires network connectivity to targets

## 🤝 Contributing

Contributions are welcome! Areas for potential improvement:
- UDP port scanning support
- Enhanced service fingerprinting
- Export to additional formats (CSV, XML)
- Scheduling and automation features
- Advanced reporting and visualization
- Performance optimizations

## 📝 License

This project is open source. Please ensure compliance with local laws and regulations when using this tool.

## 🆘 Troubleshooting

### Common Issues

1. **"Permission denied" errors**:
   - Some systems require elevated privileges for certain port operations
   - Try running with appropriate permissions if needed

2. **Slow scanning performance**:
   - Reduce timeout values for faster (but potentially less accurate) scans
   - Consider smaller IP ranges or port sets
   - Check network connectivity and latency

3. **Application won't start**:
   - Ensure all dependencies are installed: `pip install -r requirements.txt`
   - Check Python version compatibility (3.7+)
   - Verify Streamlit installation: `streamlit --version`

4. **False negatives (missing open ports)**:
   - Increase timeout values
   - Check for firewalls or network filtering
   - Verify target IP addresses are reachable

### Getting Help
- Check the scan history for previous successful configurations
- Review timeout and target settings
- Ensure network connectivity to target addresses
- Verify port ranges are within valid bounds (1-65535)

---

**Made with ❤️ by [Rounak Dey](https://github.com/rounakdey2003)**
