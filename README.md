# azure-vm-scale-sets
Study notes covering Azure VM Scale Sets, orchestration modes (Flexible vs Uniform), autoscaling and high availability configurations for AZ-104 exam preparation.

# Azure VM Scale Sets

## Objective
Understand and document Azure Virtual Machine Scale Sets (VMSS) including
orchestration modes, autoscaling, and high availability configurations.

## Key Concepts

### What is a VM Scale Set?
A VM Scale Set allows you to deploy and manage a group of load-balanced 
VMs that can automatically scale in or out based on demand or a schedule. 
It ensures high availability and performance for applications.

---

## Orchestration Modes

### Flexible Orchestration (Recommended)
- Recommended and default mode by Microsoft
- Supports autoscaling — automatically adds or removes VMs based on rules
- VMs are visible individually in the Azure Portal
- Supports Availability Zones for high availability
- Best for production workloads requiring autoscaling

### Uniform Orchestration
- All VMs are identical — same size, same image, same configuration
- Manual scaling only — does not support autoscaling
- VMs are not visible individually in the portal
- Being phased out — Flexible is now recommended

### Key Differences

| Feature | Flexible | Uniform |
|---------|----------|---------|
| Autoscaling | Yes | No — manual only |
| VM visibility | Individual VMs visible | Not visible individually |
| VM configurations | Can be different | Must be identical |
| Availability Zones | Full support | Limited |
| Recommended | Yes — default | No — being phased out |

---

## Scaling Types

### Manual Scaling
- You set the number of VM instances yourself
- No automatic adjustment
- Available in both Flexible and Uniform

### Autoscaling (Flexible Only)
- Azure automatically adds VMs when demand increases (Scale Out)
- Azure automatically removes VMs when demand decreases (Scale In)
- Based on rules — CPU usage, memory, schedule or custom metrics

### Scaling Directions
- **Scale Out** — add more VM instances when demand increases
- **Scale In** — remove VM instances when demand decreases
- **Scale Up** — increase VM size (more CPU/RAM)
- **Scale Down** — decrease VM size

---

## Important Settings

| Setting | Description |
|---------|-------------|
| Minimum instances | Least number of VMs always running |
| Maximum instances | Most VMs allowed (up to 1000) |
| Default instances | Starting number of VMs |
| Scale out rule | When to add VMs e.g. CPU greater than 75% |
| Scale in rule | When to remove VMs e.g. CPU less than 25% |
| Cool down period | Wait time between scaling actions |

---

## VM Scale Sets vs Single VM vs Availability Set

| Feature | Single VM | Availability Set | VM Scale Set |
|---------|-----------|-----------------|--------------|
| Number of VMs | 1 | 2+ | 2 to 1000 |
| Autoscaling | No | No | Yes (Flexible) |
| Load balancer | Optional | Optional | Built in |
| Use case | Single workload | HA within datacenter | High traffic apps |

---

## Tasks Completed
- [x] Studied Flexible vs Uniform orchestration modes
- [x] Understood autoscaling rules and triggers
- [x] Understood Scale Out vs Scale In vs Scale Up vs Scale Down
- [x] Understood minimum, maximum and default instance settings
- [x] Compared VM Scale Sets vs Availability Sets vs Single VMs

---

## Key Exam Scenarios

**Scenario 1:**
You need to automatically add VMs when CPU exceeds 80%.
What orchestration mode should you use?
- Answer: Flexible — only Flexible supports autoscaling

**Scenario 2:**
You need identical VMs with manual scaling only.
What orchestration mode should you use?
- Answer: Uniform orchestration

**Scenario 3:**
What is the maximum number of VM instances in a Scale Set?
- Answer: 1000

**Scenario 4:**
You need VMs to scale automatically based on a schedule.
What feature do you configure?
- Answer: Autoscale rules with schedule-based scaling in Flexible mode

---

## Important Notes
- Always use Flexible orchestration for new deployments
- Autoscaling only works with Flexible orchestration
- Uniform is being phased out — Microsoft recommends Flexible
- Scale Sets integrate with Azure Load Balancer and Application Gateway
- Delete the Resource Group after every lab to avoid charges

## References
- [VM Scale Sets Documentation](https://learn.microsoft.com/en-us/azure/virtual-machine-scale-sets/)
- [Flexible Orchestration](https://learn.microsoft.com/en-us/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-orchestration-modes)
- [Autoscale Documentation](https://learn.microsoft.com/en-us/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-autoscale-overview)
- [AZ-104 Study Guide](https://learn.microsoft.com/en-us/certifications/exams/az-104)
