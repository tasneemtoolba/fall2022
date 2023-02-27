## Main Execution Cycle of KVM:
In `/arch/x86/kvm/vmx.c` starting from `module_init(vmx_init)`

- Then `vmx_init`(defined in `/arch/x86/kvm/vmx.c`) calls kvm_init(defined in `/arch/x86/kvm/vmx.c`).
- The kvm starts initialization process in the function `kvm_init`. In addition, `kvm_init` calls `kvm_arch_init`(defined in `/arch/x86/kvm/x86.c`) that performs some KVM checks(for example, that hardware virtualization is enabled), inits mmu module and etc.
- Then `kvm_init` calls a function `kvm_vcpu_compat_ioctl`(defined in `/virt/kvm/kvm_main.c`) through the static structure `kvm_vcpu_fops`(`.compat_ioctl` property).
- After it, there `kvm_vcpu_compat_ioctl` calls another function `kvm_vcpu_ioctl`(defined in `/virt/kvm/kvm_main.c`).
- Then, `kvm_vcpu_ioctl` calls the function `kvm_arch_vcpu_ioctl_run`(defined in `/arch/x86/kvm/x86.c`).
- Finally, a function where the looping is performed is called `__vcpu_run`(defined in `/arch/x86/kvm/x86.c`). It is called from `kvm_vcpu_ioctl`.


## PF (Page Fault) Processing:
The global exception handler that resides in the function `handle_exception`(defined in `/arch/x86/kvm/vmx.c`). It checks that page fault occurred via calling function `is_page_fault`(defined in the same file).

Exploring the call chain:
`handle_exception` calls the function `kvm_mmu_page_fault` (defined in `/arch/x86/kvm/mmu.c`).
After it, `kvm_mmu_page_fault` calls function `page_fault`(defined in `/arch/x86/kernel/entry_32.S`).

## Entry and Exit Point of the Guest:
The entry point of the guest is the function `kvm_arch_vcpu_run()` in `arch/x86/kvm/x86.c`. This function sets up the initial state of the guest VM and starts its execution by calling the function `kvm_vcpu_run()`.

The exit point of the guest is the function `kvm_vcpu_exit()` in the same file. This function is called after the guest VM completes its execution, is suspended or shut down, or when a VM exit occurs. The hypervisor can then save the guest's state, shut down the virtual machine, and free any resources that were allocated to it.