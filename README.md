Kaden's Talos Kubernetes Cluster

Welcome to the infrastructure repository for my Kubernetes cluster. This repository serves as the central hub for the cluster's configuration, deployment manifests, and infrastructure-as-code, utilizing Talos Linux as the container-optimized operating system.
The Philosophy: Why Talos Linux?

This cluster is intentionally designed to move away from managing a traditional, general-purpose operating system beneath Kubernetes. I lean heavily toward minimal, highly performant, and secure environments, which makes Talos the perfect foundation for this lab.

Here is why this stack is incredibly effective and why I prefer it:

    True Immutability: Talos runs entirely from memory and uses a read-only file system. The OS is treated as a disposable, ephemeral component. If a node degrades, I don't troubleshoot the OS; I just reboot or replace it.

    Security by Design (No SSH): There is no SSH daemon, no shell, and no console access. Everything is managed strictly through a single, authenticated gRPC API. This drastically reduces the attack surface and enforces a zero-trust, API-first administration model.

    Extreme Minimalism: There is no package manager, no systemd, and zero OS bloat. The operating system includes strictly what is required to run containerd and Kubernetes, and nothing else. This translates to incredibly fast boot times and maximum compute resources dedicated entirely to the workloads.

    Declarative from the Metal Up: Instead of writing bash scripts or Ansible playbooks to configure the underlying nodes, the entire OS configuration (networking, storage, kernel parameters) is defined in a single YAML file.

Cluster Architecture & Hardware

The cluster is built for high availability and low overhead, ensuring the infrastructure stays out of the way of the actual deployments.

Hardware used is a Lenovo m720q and 2x m70q gen2