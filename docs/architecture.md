# System Architecture

## Overview
DevOps Simulator follows a *microservices architecture* designed for high availability, scalability, and flexibility across both production and development environments.

---

## Environments

### 🟢 Production
- *Purpose:* Stable, high-performance deployment for end users  
- *Version:* 1.0.0  
- *Deployment:* Kubernetes (rolling updates, zero downtime)

#### Components
*1. Application Server*
- Technology: Node.js + Express  
- Port: 8080  
- Scaling: Horizontal auto-scaling enabled  

*2. Database Layer*
- Database: PostgreSQL 14  
- Configuration: Master-slave replication  
- Backup: Automated daily backups  

*3. Monitoring System*
- Tool: Prometheus + Grafana  
- Metrics: CPU, Memory, Disk, Network  
- Alerts: Email notifications for critical issues  

#### Deployment Strategy
- Method: Rolling updates  
- Zero-downtime: ✅ Yes  
- Rollback: Automated on failure  

#### Security
- SSL/TLS encryption  
- Database connection encryption  
- Regular security audits  

---

### 🧪 Development
- *Purpose:* Experimental setup for testing new features  
- *Version:* 2.0.0-beta  
- *Deployment:* Docker Compose (local development)

#### Components
*1. Application Server*
- Technology: Node.js + Express (with hot reload)  
- Port: 3000  
- Scaling: Single instance (manual)  
- Debug: Chrome DevTools on port 9229  

*2. Database Layer*
- Database: PostgreSQL 14 (local instance)  
- Configuration: Single instance (no replication)  
- Backup: Manual only  
- Seeding: Auto-seed test data on startup  

*3. Monitoring System*
- Tool: Console logging + optional Prometheus  
- Metrics: CPU, Memory, Disk, Network, Build time  
- Alerts: Console warnings (no emails)  
- Dashboard: In-development web dashboard  

*4. Container Orchestration*
- Tool: Docker Compose  
- Services: App, Database, Redis cache  
- Volume Mounts: Code directory (for hot reload)  

*5. Authentication System (Beta)*
- Method: OAuth2 + JWT  
- Providers: Google, GitHub  
- Sessions: Redis-based  

#### Deployment Strategy
- Method: Docker Compose hot reload  
- Zero-downtime: ❌ Not applicable  
- Rollback: Git checkout previous commit  

#### Security
- SSL/TLS disabled (local only)  
- Credentials in plain text (dev only)  
- CORS enabled for all origins  
- Debug endpoints exposed  

#### Experimental Features
⚠ Warning – these are unstable:  
- Multi-cloud deployment  
- AI-powered log analysis  
- Automatic rollback on anomaly detection