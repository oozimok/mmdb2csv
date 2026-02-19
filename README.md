# mmdb2csv

# What does it do?

Convert Maxmind mmdb database to CSV.

# Supported Databases

Automatically detects database type based on filename:
- City
- Country
- Connections
- ISP
- ASN **(New!)**

# Advanced Filtering

You can filter the output by any field value using the following flags:
- `-filter-field`: The name of the field to filter by (e.g., `autonomous_system_organization` or `prefix`).
- `-filter-value`: The value to search for.

## Filtering Features
- **Substring Match**: Filters match any part of the field value (case-insensitive).
- **IP Lookup**: If filtering by the `prefix` field with a specific IP address, the tool finds the CIDR range that contains that IP.

# Examples

## Basic conversion
```bash
./mmdb2csv GeoLite2-ASN.mmdb > asn.csv
```

## Filter by organization (substring)
```bash
./mmdb2csv -filter-field autonomous_system_organization -filter-value "Opera Norway" GeoLite2-ASN.mmdb
```

## IP address lookup
```bash
./mmdb2csv -filter-field prefix -filter-value "82.145.223.76" GeoLite2-ASN.mmdb
```

# Build
```bash
go build mmdb2csv.go
```
