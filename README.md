# 📦 Configuration Package – City Health Clinic Queue Management System
**Version:** 1.0  
**Prepared By:** Kaleb   
**Date:** 1/10/2026  
**Environment:** Mock Configuration (Portfolio Project)

---

## 1. System Overview
The City Health Clinic Queue Management System is configured to support patient check-in, queue prioritization, staff workflow management, and SMS notifications. Patients check in via kiosk, select a service type, and are placed into a prioritized queue. Staff manage patient flow through a real-time dashboard, and the system logs timestamps for reporting and operational insights.

---

## 2. Service Types Configuration

| Service Type | Description | Priority Level | Active | Notes |
|--------------|-------------|----------------|--------|-------|
| **New Patient** | First-time visitors requiring full intake | 2 (Lower) | Yes | Longer processing time expected |
| **Returning Patient** | Existing patients with prior records | 1 (Higher) | Yes | Prioritized over new patients |
| **Prescription Pickup** | Patients picking up medication only | 3 (Lowest) | Yes | Fast service; no prioritization |

---

## 3. Queue Prioritization Rules

### **Rule Set: Priority Assignment**
- **Rule 1:** Returning Patients (Priority 1) are placed ahead of New Patients (Priority 2) when arrival times are within a 5-minute threshold.  
- **Rule 2:** Prescription Pickup (Priority 3) is always placed at the end of the queue unless no other patients are waiting.  
- **Rule 3:** If two patients share the same priority, FIFO (First-In, First-Out) applies.  
- **Rule 4:** Staff may override queue order manually (Supervisor role required).

---

## 4. SMS Notification Configuration

### **Enabled:** Yes  
### **SMS Provider:** Mock SMS Gateway (Portfolio Simulation)

| Event Trigger | Description | Message Template |
|---------------|-------------|------------------|
| **Next in Queue** | Patient is next to be called | “You’re next in line. Please be prepared.” |
| **Called to Room** | Staff updates status to “Called” | “Please proceed to Room {{room_number}}.” |
| **Delay Notification** | Queue delays detected | “We’re experiencing a short delay. Thank you for your patience.” |

**Phone Number Capture:**  
- Optional field on kiosk  
- Validated for 10-digit format  
- Stored only for duration of visit  

---

## 5. Staff Dashboard Configuration

### **Dashboard Views**

| View Name | Description | Fields Displayed |
|-----------|-------------|------------------|
| **All Patients** | Full queue list | Name/Ticket, Service Type, Check-In Time, Status |
| **By Service Type** | Filtered view | Same as above |
| **In Room** | Patients currently being served | Name/Ticket, Room, Status |
| **Completed** | End-of-day review | Name/Ticket, Service Type, Total Time |

### **Status Options**
- Waiting  
- Next  
- Called  
- In Room  
- Completed  

### **Permissions**

| Role | Permissions |
|------|-------------|
| **Staff** | View queue, update status |
| **Supervisor** | Override queue order, edit service types |
| **Admin** | Full configuration access |

---

## 6. Data Logging & Reporting Configuration

### **Data Captured**

| Data Point | Description |
|------------|-------------|
| Check-In Timestamp | When patient completes kiosk check-in |
| Status Change Timestamp | When staff update patient status |
| Service Type | Selected by patient |
| Queue Position | Calculated by system |
| SMS Sent Events | Logged for audit |

### **Reporting Outputs**
- Daily patient volume by service type  
- Average wait time  
- Average service time  
- SMS delivery success rate  
- Queue bottleneck identification  

---

## 7. Security & Access Controls

### **Authentication**
- Dashboard login required  
- Session timeout: 15 minutes  

### **Data Handling**
- Phone numbers stored temporarily  
- No PHI stored in mock system  
- Logs retained for 30 days  

### **Role-Based Access**
- Staff: Basic queue management  
- Supervisor: Overrides + escalations  
- Admin: Full configuration  

---

## 8. Version History & Change Log

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 1.0 | 1/10/2026 | Kaleb B | Initial configuration package created |

---
