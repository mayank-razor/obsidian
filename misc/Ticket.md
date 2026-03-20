P0 - Highest 4hr
P1 - high 8hr
P2 - 8 days (working days)

either solve it or forward to dev

TAM(swiggy zomato) -> priorities wil be of P0 and P1 type
To learn the complete payment flow code-wise, I'll help you create a structured learning path. Let me first explore the codebase to understand the entry points and flow.


[15 tools called]

Based on my analysis of the codebase, here's a comprehensive learning path to understand the complete payment flow code-wise:

## 🎯 **Complete Payment Flow Learning Path**

### **Phase 1: Entry Points & API Layer (Start Here)**

**1. API Service Entry Points**
- **File**: `api/app/Http/Controllers/PaymentCreateController.php`
- **Key Methods**: 
  - `postCreatePayment()` - Main payment creation endpoint
  - `postAJAX()` - AJAX payment creation
  - `coreCreatePayment()` - Core payment processing logic
- **Purpose**: Entry point for all payment requests

**2. Payment Processing Service**
- **File**: `api/app/Models/Payment/Service.php`
- **Key Methods**: `process()` - Main payment processing orchestrator
- **Purpose**: Central payment service that coordinates the entire flow

### **Phase 2: Payment Entity Creation & Validation**

**3. Payment Processor**
- **File**: `api/app/Models/Payment/Processor/Processor.php`
- **Key Methods**: 
  - `process()` - Main processing logic
  - `buildPaymentEntity()` - Creates payment entity
  - `preProcessPaymentInputs()` - Input validation
- **Purpose**: Handles payment entity creation and initial processing

**4. Payment Authorization**
- **File**: `api/app/Models/Payment/Processor/Authorize.php`
- **Key Methods**:
  - `authorize()` - Main authorization logic
  - `coreAuthorize()` - Core authorization processing
  - `gatewayRelatedProcessing()` - Gateway interaction
- **Purpose**: Handles payment authorization with gateways

### **Phase 3: Gateway Communication & Routing**

**5. PG-Router Service**
- **File**: `pg-router/internal/payments/service.go`
- **Key Methods**: `PaymentCreate()` - Payment routing logic
- **Purpose**: Routes payments to appropriate services (CPS, Mozart, etc.)

**6. PG-Router Routing Logic**
- **File**: `pg-router/internal/payments/proxy/can_route.go`
- **Key Methods**: `IsPGRouterSupportBasedOnReqBody()` - Routing decisions
- **Purpose**: Determines which service should handle the payment

### **Phase 4: Card Payment Processing (CPS)**

**7. Card Payment Service - Initiate**
- **File**: `payments-card/internal/payment/processor/initiate.go`
- **Key Methods**: `Initiate()` - Card payment initiation
- **Purpose**: Handles card payment processing logic

**8. Card Payment Service - Core**
- **File**: `payments-card/v2/cards/payment/core.go`
- **Purpose**: Core card payment processing functionality

### **Phase 5: Gateway Communication (Mozart)**

**9. Mozart Gateway Configuration**
- **File**: `mozart/conf/gatewayConfig.json`
- **Purpose**: Gateway endpoint configurations and routing

**10. Mozart Express Configuration**
- **File**: `mozart/expressConf/gatewayConfig.json`
- **Purpose**: Express gateway configurations

### **Phase 6: Payment Callback & Verification**

**11. Payment Callback Processing**
- **File**: `api/app/Models/Payment/Processor/Callback.php`
- **Key Methods**: `callback()` - Handles gateway callbacks
- **Purpose**: Processes responses from payment gateways

**12. Gateway Controller**
- **File**: `api/app/Http/Controllers/GatewayController.php`
- **Key Methods**: `callbackGateway()` - Gateway callback routing
- **Purpose**: Routes callbacks to appropriate processors

**13. Payment Verification**
- **File**: `api/app/Models/Payment/Service.php`
- **Key Methods**: `verifyPayment()` - Payment verification
- **Purpose**: Verifies payment status with gateways

### **Phase 7: Post-Processing & Completion**

**14. Payment Capture**
- **File**: `payments-card/internal/payment/processor/capture.go`
- **Purpose**: Handles payment capture after authorization

**15. Payment Status Updates**
- **File**: `api/app/Models/Payment/Processor/Authorize.php`
- **Key Methods**: `postPaymentAuthorizeProcessing()` - Post-authorization processing
- **Purpose**: Handles post-authorization tasks like notifications, settlements

## 🚀 **Recommended Learning Sequence**

### **Week 1: Foundation**
1. Start with `PaymentCreateController.php` - understand entry points
2. Study `Payment/Service.php` - understand main orchestration
3. Explore `Payment/Processor/Processor.php` - understand entity creation

### **Week 2: Authorization & Routing**
4. Deep dive into `Payment/Processor/Authorize.php` - understand authorization flow
5. Study PG-Router routing logic in `can_route.go`
6. Understand PG-Router service in `service.go`

### **Week 3: Card Processing**
7. Explore `payments-card/internal/payment/processor/initiate.go`
8. Study card payment core in `v2/cards/payment/core.go`
9. Understand Mozart gateway configurations

### **Week 4: Callbacks & Verification**
10. Study callback processing in `Payment/Processor/Callback.php`
11. Understand gateway controller routing
12. Explore payment verification logic

### **Week 5: Advanced Topics**
13. Study capture processing
14. Understand post-authorization processing
15. Explore error handling and edge cases

## 🔍 **Key Concepts to Focus On**

1. **Payment States**: Created → Authorized → Captured
2. **Service Communication**: API → PG-Router → CPS/Mozart → Gateway
3. **Callback Flow**: Gateway → Callback → Verification → Status Update
4. **Error Handling**: How failures are handled at each stage
5. **Routing Logic**: How payments are routed to different services

## 📚 **Additional Resources**

- **API Routes**: Check `api/routes/` for endpoint definitions
- **Database Models**: Study `api/app/Models/Payment/Entity.php`
- **Gateway Implementations**: Explore `api/app/Gateway/` directory
- **Configuration**: Check service-specific config files

This learning path will give you a comprehensive understanding of the entire payment flow from user action to completion, covering all the major services and their interactions.
