# Prooflane SDKs (TypeScript/Dart)

## 🎯 **Repository Purpose**

The Prooflane SDKs repository serves as the **client library hub** for the entire Sealfold organization. It provides language-specific client libraries that enable developers to easily integrate with the proof-of-lane verification system, ensuring consistent API access across multiple programming languages and platforms.

## 🏗️ **Core Responsibilities**

### **Multi-Language Support**
- **TypeScript/JavaScript**: Primary SDK for web and Node.js applications
- **Dart**: Mobile and cross-platform application support
- **Python**: Data science and automation integration
- **Java**: Enterprise and Android application support
- **.NET**: Windows and enterprise application support
- **Go**: High-performance and cloud-native applications

### **API Client Libraries**
- **HTTP Client**: RESTful API client implementations
- **GraphQL Client**: GraphQL query and mutation support
- **WebSocket Client**: Real-time communication capabilities
- **Authentication**: Secure authentication and authorization handling

### **Developer Experience**
- **Type Safety**: Comprehensive type definitions and interfaces
- **Error Handling**: Consistent error handling across all languages
- **Documentation**: Language-specific documentation and examples
- **Testing**: Comprehensive test suites for all SDKs

## 🔧 **Technical Architecture**

### **SDK Architecture**
```typescript
// Core SDK structure
interface ProoflaneSDK {
  // Core services
  verifications: VerificationService;
  workflows: WorkflowService;
  users: UserService;
  analytics: AnalyticsService;
  
  // Configuration
  config: SDKConfig;
  
  // Utilities
  utils: SDKUtils;
}
```

### **Language-Specific Implementations**
```
┌─────────────────────────────────────────────────────────┐
│                    PROOFLANE SDKs                      │
├─────────────────────────────────────────────────────────┤
│  • TypeScript/JavaScript SDK                          │
│  • Dart SDK                                           │
│  • Python SDK                                         │
│  • Java SDK                                           │
│  • .NET SDK                                           │
│  • Go SDK                                             │
└─────────────────────────────────────────────────────────┘
```

## 🔗 **Dependencies & Relationships**

### **Dependencies**
- **prooflane-spec**: Must implement specification-defined interfaces
- **sealfold-server**: Must consume backend APIs correctly

### **Dependents**
- **prooflane-viewer**: Frontend uses TypeScript SDK
- **sealfold-studio-lite**: Development tools use multiple SDKs
- **sealfold-bridge-sharepoint**: Integration uses appropriate SDKs
- **sealfold-vector-sync**: Vector operations may use SDKs

## 🧠 **AI Agent Integration**

### **SDK Agent**
The repository includes a specialized AI agent (`sdk-agent.md`) that:
- **API Compatibility**: Ensures SDK compatibility with backend APIs
- **Multi-Language Coordination**: Manages consistency across all language SDKs
- **Performance Optimization**: Optimizes SDK performance and efficiency
- **Quality Assurance**: Ensures SDK quality and reliability

### **Agent Capabilities**
- **API Validation**: Validates SDK implementations against specifications
- **Cross-Language Testing**: Tests consistency across all language SDKs
- **Performance Monitoring**: Monitors SDK performance and optimization
- **Integration Testing**: Tests SDK integration with dependent repositories

## 📁 **Repository Structure**

```
prooflane-sdks/
├── typescript/              # TypeScript/JavaScript SDK
│   ├── src/                 # Source code
│   ├── tests/               # Test suites
│   ├── examples/            # Usage examples
│   └── package.json         # Package configuration
├── dart/                    # Dart SDK
│   ├── lib/                 # Source code
│   ├── test/                # Test suites
│   ├── example/             # Usage examples
│   └── pubspec.yaml         # Package configuration
├── python/                  # Python SDK
│   ├── src/                 # Source code
│   ├── tests/               # Test suites
│   ├── examples/            # Usage examples
│   └── setup.py             # Package configuration
├── java/                    # Java SDK
│   ├── src/                 # Source code
│   ├── test/                # Test suites
│   ├── examples/            # Usage examples
│   └── pom.xml              # Package configuration
├── dotnet/                  # .NET SDK
│   ├── src/                 # Source code
│   ├── tests/               # Test suites
│   ├── examples/            # Usage examples
│   └── ProoflaneSDK.csproj # Project configuration
├── go/                      # Go SDK
│   ├── cmd/                 # Command line tools
│   ├── internal/            # Internal packages
│   ├── pkg/                 # Public packages
│   ├── test/                # Test suites
│   └── go.mod               # Module configuration
├── .cursor/
│   └── rules/               # Cursor agent rules
│       ├── sdk-agent.md     # SDK agent rules
│       ├── org-guardrails.md # Organization guardrails
│       └── README.md        # Cursor rules overview
├── CURSOR.md                # Cursor configuration
└── README.md                # This file
```

## 🚀 **Getting Started**

### **TypeScript/JavaScript SDK**
```bash
# Install via npm
npm install @prooflane/sdk

# Install via yarn
yarn add @prooflane/sdk

# Basic usage
import { ProoflaneSDK } from '@prooflane/sdk';

const sdk = new ProoflaneSDK({
  apiKey: 'your-api-key',
  baseUrl: 'https://api.sealfold.org'
});

// Create verification
const verification = await sdk.verifications.create({
  title: 'Sample Verification',
  description: 'This is a sample verification'
});
```

### **Dart SDK**
```yaml
# pubspec.yaml
dependencies:
  prooflane_sdk: ^1.0.0

# Basic usage
import 'package:prooflane_sdk/prooflane_sdk.dart';

void main() async {
  final sdk = ProoflaneSDK(
    apiKey: 'your-api-key',
    baseUrl: 'https://api.sealfold.org',
  );
  
  final verification = await sdk.verifications.create(
    title: 'Sample Verification',
    description: 'This is a sample verification',
  );
}
```

### **Python SDK**
```bash
# Install via pip
pip install prooflane-sdk

# Basic usage
from prooflane_sdk import ProoflaneSDK

sdk = ProoflaneSDK(
    api_key='your-api-key',
    base_url='https://api.sealfold.org'
)

# Create verification
verification = sdk.verifications.create(
    title='Sample Verification',
    description='This is a sample verification'
)
```

## 🔌 **API Client Features**

### **HTTP Client Implementation**
```typescript
// TypeScript SDK HTTP client
class HTTPClient {
  private baseURL: string;
  private apiKey: string;
  private headers: Record<string, string>;

  constructor(config: ClientConfig) {
    this.baseURL = config.baseUrl;
    this.apiKey = config.apiKey;
    this.headers = {
      'Authorization': `Bearer ${this.apiKey}`,
      'Content-Type': 'application/json'
    };
  }

  async request<T>(options: RequestOptions): Promise<T> {
    const response = await fetch(`${this.baseURL}${options.path}`, {
      method: options.method,
      headers: this.headers,
      body: options.body ? JSON.stringify(options.body) : undefined
    });

    if (!response.ok) {
      throw new ProoflaneError(response.status, response.statusText);
    }

    return response.json();
  }
}
```

### **GraphQL Client Support**
```typescript
// GraphQL client implementation
class GraphQLClient {
  async query<T>(query: string, variables?: any): Promise<T> {
    const response = await this.request({
      method: 'POST',
      path: '/graphql',
      body: {
        query,
        variables
      }
    });

    return response.data;
  }

  async mutation<T>(mutation: string, variables?: any): Promise<T> {
    const response = await this.request({
      method: 'POST',
      path: '/graphql',
      body: {
        query: mutation,
        variables
      }
    });

    return response.data;
  }
}
```

### **WebSocket Client**
```typescript
// WebSocket client for real-time updates
class WebSocketClient {
  private ws: WebSocket;
  private reconnectAttempts = 0;
  private maxReconnectAttempts = 5;

  connect(url: string) {
    this.ws = new WebSocket(url);
    this.ws.onmessage = this.handleMessage.bind(this);
    this.ws.onclose = this.handleClose.bind(this);
  }

  private handleMessage(event: MessageEvent) {
    const data = JSON.parse(event.data);
    this.emit('message', data);
  }

  private handleClose() {
    if (this.reconnectAttempts < this.maxReconnectAttempts) {
      setTimeout(() => this.reconnect(), 1000 * Math.pow(2, this.reconnectAttempts));
      this.reconnectAttempts++;
    }
  }
}
```

## 📊 **Service Implementations**

### **Verification Service**
```typescript
// Verification service interface
interface VerificationService {
  create(data: CreateVerificationData): Promise<Verification>;
  get(id: string): Promise<Verification>;
  update(id: string, data: UpdateVerificationData): Promise<Verification>;
  delete(id: string): Promise<void>;
  list(filters?: VerificationFilters): Promise<VerificationList>;
}

// TypeScript implementation
class VerificationServiceImpl implements VerificationService {
  async create(data: CreateVerificationData): Promise<Verification> {
    return this.client.request({
      method: 'POST',
      path: '/verifications',
      body: data
    });
  }

  async get(id: string): Promise<Verification> {
    return this.client.request({
      method: 'GET',
      path: `/verifications/${id}`
    });
  }

  async update(id: string, data: UpdateVerificationData): Promise<Verification> {
    return this.client.request({
      method: 'PUT',
      path: `/verifications/${id}`,
      body: data
    });
  }

  async delete(id: string): Promise<void> {
    await this.client.request({
      method: 'DELETE',
      path: `/verifications/${id}`
    });
  }

  async list(filters?: VerificationFilters): Promise<VerificationList> {
    const queryParams = new URLSearchParams();
    if (filters) {
      Object.entries(filters).forEach(([key, value]) => {
        if (value !== undefined) {
          queryParams.append(key, String(value));
        }
      });
    }

    return this.client.request({
      method: 'GET',
      path: `/verifications?${queryParams.toString()}`
    });
  }
}
```

### **Workflow Service**
```typescript
// Workflow service interface
interface WorkflowService {
  create(data: CreateWorkflowData): Promise<Workflow>;
  get(id: string): Promise<Workflow>;
  update(id: string, data: UpdateWorkflowData): Promise<Workflow>;
  delete(id: string): Promise<void>;
  execute(id: string, input?: any): Promise<WorkflowExecution>;
  list(filters?: WorkflowFilters): Promise<WorkflowList>;
}

// Implementation
class WorkflowServiceImpl implements WorkflowService {
  async execute(id: string, input?: any): Promise<WorkflowExecution> {
    return this.client.request({
      method: 'POST',
      path: `/workflows/${id}/execute`,
      body: { input }
    });
  }

  // ... other methods
}
```

## 🧪 **Testing Strategy**

### **Test Types**
- **Unit Tests**: Individual service and utility testing
- **Integration Tests**: API integration testing
- **Language Tests**: Language-specific functionality testing
- **Performance Tests**: SDK performance testing
- **Compatibility Tests**: Cross-version compatibility testing

### **Testing Configuration**
```typescript
// Test setup for TypeScript SDK
import { describe, it, expect, beforeEach, vi } from 'vitest';

// Mock HTTP client
vi.mock('../http-client', () => ({
  HTTPClient: vi.fn().mockImplementation(() => ({
    request: vi.fn()
  }))
}));

// Test verification service
describe('VerificationService', () => {
  let service: VerificationService;
  let mockClient: any;

  beforeEach(() => {
    mockClient = new HTTPClient({} as any);
    service = new VerificationServiceImpl(mockClient);
  });

  it('should create verification successfully', async () => {
    const mockVerification = { id: '1', title: 'Test' };
    mockClient.request.mockResolvedValue(mockVerification);

    const result = await service.create({ title: 'Test' });
    expect(result).toEqual(mockVerification);
  });
});
```

## 📊 **Performance Optimization**

### **Connection Pooling**
```typescript
// Connection pool for HTTP clients
class ConnectionPool {
  private pool: HTTPClient[] = [];
  private maxConnections: number;
  private currentConnections: number = 0;

  constructor(maxConnections: number = 10) {
    this.maxConnections = maxConnections;
  }

  async getConnection(): Promise<HTTPClient> {
    if (this.pool.length > 0) {
      return this.pool.pop()!;
    }

    if (this.currentConnections < this.maxConnections) {
      this.currentConnections++;
      return new HTTPClient({} as any);
    }

    // Wait for available connection
    return new Promise((resolve) => {
      const checkPool = () => {
        if (this.pool.length > 0) {
          resolve(this.pool.pop()!);
        } else {
          setTimeout(checkPool, 100);
        }
      };
      checkPool();
    });
  }

  releaseConnection(client: HTTPClient) {
    this.pool.push(client);
  }
}
```

### **Caching Layer**
```typescript
// Caching implementation
class CacheManager {
  private cache = new Map<string, { data: any; expiry: number }>();
  private ttl: number;

  constructor(ttl: number = 5 * 60 * 1000) { // 5 minutes default
    this.ttl = ttl;
  }

  get(key: string): any | null {
    const item = this.cache.get(key);
    if (!item) return null;

    if (Date.now() > item.expiry) {
      this.cache.delete(key);
      return null;
    }

    return item.data;
  }

  set(key: string, data: any, ttl?: number): void {
    const expiry = Date.now() + (ttl || this.ttl);
    this.cache.set(key, { data, expiry });
  }

  clear(): void {
    this.cache.clear();
  }
}
```

## 🔒 **Security Features**

### **Authentication Handling**
```typescript
// Authentication manager
class AuthManager {
  private apiKey: string;
  private refreshToken?: string;
  private accessToken?: string;

  constructor(apiKey: string) {
    this.apiKey = apiKey;
  }

  async authenticate(): Promise<string> {
    if (this.accessToken && !this.isTokenExpired(this.accessToken)) {
      return this.accessToken;
    }

    if (this.refreshToken && !this.isTokenExpired(this.refreshToken)) {
      return this.refreshAccessToken();
    }

    return this.authenticateWithApiKey();
  }

  private async authenticateWithApiKey(): Promise<string> {
    const response = await fetch('/auth/api-key', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ apiKey: this.apiKey })
    });

    const { accessToken, refreshToken } = await response.json();
    this.accessToken = accessToken;
    this.refreshToken = refreshToken;

    return accessToken;
  }
}
```

### **Request Signing**
```typescript
// Request signing for enhanced security
class RequestSigner {
  private secretKey: string;

  constructor(secretKey: string) {
    this.secretKey = secretKey;
  }

  signRequest(method: string, path: string, body?: any): string {
    const timestamp = Date.now().toString();
    const payload = `${method}${path}${timestamp}${body ? JSON.stringify(body) : ''}`;
    
    return crypto
      .createHmac('sha256', this.secretKey)
      .update(payload)
      .digest('hex');
  }
}
```

## 🚀 **Deployment & Distribution**

### **Package Distribution**
```json
// TypeScript SDK package.json
{
  "name": "@prooflane/sdk",
  "version": "1.0.0",
  "main": "dist/index.js",
  "types": "dist/index.d.ts",
  "scripts": {
    "build": "tsc",
    "test": "vitest",
    "publish": "npm publish"
  },
  "files": [
    "dist",
    "README.md",
    "LICENSE"
  ]
}
```

### **CI/CD Pipeline**
```yaml
# GitHub Actions workflow
name: Build and Test SDKs

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  build-typescript:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: '18'
      - run: npm ci
      - run: npm run build
      - run: npm test
      - run: npm run lint

  build-dart:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: dart-lang/setup-dart@v1
      - run: dart pub get
      - run: dart analyze
      - run: dart test
```

## 🔮 **Future Enhancements**

### **Phase 1: Core SDKs (Current)**
- ✅ TypeScript/JavaScript SDK
- ✅ Dart SDK
- 🔄 Python SDK
- 🔄 Java SDK
- 📋 .NET SDK
- 📋 Go SDK

### **Phase 2: Advanced Features (Next Quarter)**
- 🔄 GraphQL client support
- 🔄 WebSocket real-time updates
- 🔄 Advanced caching strategies
- 🔄 Performance optimization

### **Phase 3: Enterprise Features (Future)**
- 📋 Multi-language code generation
- 📋 Advanced authentication methods
- 📋 SDK analytics and monitoring
- 📋 Automated testing and validation

## 🤝 **Contributing**

### **Development Guidelines**
- **Code Standards**: Follow language-specific coding standards
- **Testing**: Write comprehensive tests for all functionality
- **Documentation**: Update documentation for API changes
- **Cross-Language Consistency**: Maintain consistency across all SDKs

### **Development Workflow**
1. **Fork**: Fork the repository
2. **Branch**: Create feature branch for specific SDK
3. **Develop**: Implement changes with tests
4. **Test**: Ensure all tests pass across languages
5. **Submit**: Submit pull request
6. **Review**: Address review feedback
7. **Merge**: Merge approved changes

## 📞 **Support & Contact**

### **Getting Help**
- **Documentation**: Check comprehensive SDK documentation
- **Examples**: Review usage examples for each language
- **Issues**: Report issues in the repository
- **Team Support**: Contact SDK team for assistance
- **Agent Support**: Use SDK Agent for guidance

### **Team Contact**
- **SDK Team**: sdk@sealfold.org
- **Technical Questions**: tech@sealfold.org
- **General Inquiries**: info@sealfold.org

---

**Last Updated**: August 13, 2025  
**Maintained By**: Sealfold SDK Team  
**Contact**: sdk@sealfold.org

*The Prooflane SDKs repository provides the essential client libraries for integrating with the verification system. By offering consistent, high-quality SDKs across multiple programming languages, we enable developers to easily build applications that leverage the power of proof-of-lane verification.* 🚀
