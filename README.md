# Pactus gRPC Client Library

A Dart gRPC client library for seamless interaction with the **Pactus Blockchain**.  
This package provides generated gRPC code to access Pactus blockchain services efficiently.

---

## Features

- **Comprehensive gRPC Support**: Full access to all Pactus blockchain services.
- **Type-Safe Interactions**: Uses generated Protobuf classes for robust, type-safe API usage.
- **Multi-Service Integration**: Supports Blockchain, Network, Transaction, Wallet, and Utility services.
- **Cross-Platform Compatibility**: Works with both Dart and Flutter applications.

---

## Installation

Add the dependency to your `pubspec.yaml`:

```yaml
dependencies:
  flutter_pactus_grpc: ^0.1.2
```

Then fetch the package:

```bash
dart pub get
```

---

## Quick Start

Example usage of `flutter_pactus_grpc`:

```dart
import 'package:flutter_pactus_grpc/flutter_pactus_grpc.dart';

void main() {
  // Initialize blockchain service
  final blockchainService = BlockchainService();

  // Create a transaction instance
  final transaction = Transaction();

  // Initialize wallet service
  final walletService = WalletService();
}
```

---

## Services Overview

### Blockchain Service
- Retrieve blockchain metadata and status.
- Access block data and transaction history.
- Query network statistics.

### Network Service
- Monitor network topology and peer connections.
- Retrieve connection status and performance metrics.

### Transaction Service
- Create and broadcast transactions.
- Validate and query transaction details.

### Wallet Service
- Manage accounts and perform balance queries.
- Execute transfers and other wallet operations.

### Utility Service
- Access common utilities and helper functions.
- Perform cryptographic operations.

---

## Example Usage

Connecting to a Pactus node and retrieving blockchain information:

```dart
import 'package:flutter_pactus_grpc/flutter_pactus_grpc.dart';
import 'package:grpc/grpc.dart';

Future<void> connectToPactus() async {
  // Establish a gRPC channel
  final channel = ClientChannel(
    'localhost',
    port: 50051,
    options: const ChannelOptions(
      credentials: ChannelCredentials.insecure(),
    ),
  );

  // Initialize the blockchain service client
  final client = BlockchainServiceClient(channel);

  try {
    // Fetch blockchain information
    final response = await client.getBlockchainInfo(BlockchainRequest());
    print('Blockchain Height: ${response.height}');
  } catch (e) {
    print('Error: $e');
  } finally {
    // Clean up and close the channel
    await channel.shutdown();
  }
}

void main() {
  connectToPactus();
}
```

---

## API Documentation

For full API reference, visit the  
👉 [Pactus Blockchain Documentation](https://pactus.org/docs)

---

## Requirements

- **Dart SDK**: >= 3.0.0  
- **Pactus Node**: Must be running with gRPC enabled
