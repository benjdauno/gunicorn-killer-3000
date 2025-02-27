# Gunicorn Killer 3000

## Overview
The **Gunicorn Killer 3000** is a Kubernetes Job that uses `kubectl` to delete pods running Gunicorn instances that have stuck or unresponsive threads. This ensures that the affected pods are terminated and replaced by Kubernetes, restoring application availability.

## How It Works
1. A Kubernetes Job runs a container with `kubectl` installed.
2. The Job deletes pods with stuck Gunicorn threads, as identified by our alerts
3. The Job runs with a Kubernetes Service Account that has RBAC permissions to delete pods.

## This Repo Project

A devcontainer is provided so that this project can be shared across developer workstations with minimal friction. To initialize the environment.

1. Open up the project in the devContainer
2. Use `kind create cluster` to create a local kubernetes cluster.

The k8s-manifests folder contains the rbac and a job to see if the delete process works.

The dummy-deployment.yaml gives the job a target to delete.
