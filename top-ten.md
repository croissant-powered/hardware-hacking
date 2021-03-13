# Hardware security top 10

  1. No firmware updates and/or obsolete OS
  2. Debugging interfaces not removed in end product (JTAG/SWD, UART)
  3. Root console exposed by UART
  4. Insecure protocols (telnet, TFTP, Modbus)
  5. Poor access controls (passwords, ACLs, services running as root)
  6. Firmware is not signed or verified
  7. Hardcoded secrets
  8. Poor TLS (certificates are not verified)
  9. Poor RNG or cryptographic services
  10. No toolchain hardening

