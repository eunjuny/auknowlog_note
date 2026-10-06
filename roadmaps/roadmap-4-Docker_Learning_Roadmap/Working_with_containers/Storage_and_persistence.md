# Storage and Persistence
총 7문항 · 정답 7 · 오답 0

## Q1. Why is persistence important for application data in containers?
- A. It makes images smaller automatically.
  - 해설: It makes images smaller automatically.
- B. Data disappears when the container is removed.
  - 해설: Data disappears when the container is removed.
- C. Data survives container lifecycle changes.
  - 해설: Data survives container lifecycle changes.
- D. It prevents the need for backups.
  - 해설: It prevents the need for backups.
✅ 내 답: Data survives container lifecycle changes.
설명: Persistent data survives container deletion or recreation, unlike data written only inside the container filesystem.

## Q2. Which location is typically ephemeral in a Docker setup?
- A. A host bind mount.
  - 해설: A host bind mount.
- B. The container's writable layer.
  - 해설: The container's writable layer.
- C. A named volume.
  - 해설: A named volume.
- D. An external backup archive.
  - 해설: An external backup archive.
✅ 내 답: The container's writable layer.
설명: Container filesystem changes are ephemeral unless stored in a persistent location like a volume or bind mount.

## Q3. A database container is replaced during deployment. What should you use to keep its data?
- A. Use a persistent volume or bind mount.
  - 해설: Use a persistent volume or bind mount.
- B. Use the container's temporary filesystem.
  - 해설: Use the container's temporary filesystem.
- C. Rebuild the image with the same tag.
  - 해설: Rebuild the image with the same tag.
- D. Store the database files in the image.
  - 해설: Store the database files in the image.
✅ 내 답: Use a persistent volume or bind mount.
설명: Use persistent storage when data must remain available after the container is recreated.

## Q4. Which choice is usually best for mounting source code during local development?
- A. A read-only image layer.
  - 해설: A read-only image layer.
- B. A bind mount from the project directory on the host.
  - 해설: A bind mount from the project directory on the host.
- C. A tarball copied into the image.
  - 해설: A tarball copied into the image.
- D. An anonymous container filesystem.
  - 해설: An anonymous container filesystem.
✅ 내 답: A bind mount from the project directory on the host.
설명: Bind mounts are best for live editing because they map a host directory directly into the container.

## Q5. Which is the better default choice for storing a database's persistent data in Docker?
- A. The application's build context.
  - 해설: The application's build context.
- B. The container's writable layer.
  - 해설: The container's writable layer.
- C. A Docker volume.
  - 해설: A Docker volume.
- D. A temporary cache directory.
  - 해설: A temporary cache directory.
✅ 내 답: A Docker volume.
설명: Volumes are generally preferred for managed, application data because Docker handles their location and lifecycle more cleanly.

## Q6. What is the most practical way to back up data used by a Dockerized database?
- A. Restart the container before backing up.
  - 해설: Restart the container before backing up.
- B. Export the persistent volume contents or database dump.
  - 해설: Export the persistent volume contents or database dump.
- C. Delete unused images first.
  - 해설: Delete unused images first.
- D. Copy the container image only.
  - 해설: Copy the container image only.
✅ 내 답: Export the persistent volume contents or database dump.
설명: Backups are typically created from persistent storage, not from the container image or running process alone.

## Q7. How should two containers share the same data directory?
- A. Mount the same volume into both containers.
  - 해설: Mount the same volume into both containers.
- B. Copy files into each container image separately.
  - 해설: Copy files into each container image separately.
- C. Use only the container's internal filesystem.
  - 해설: Use only the container's internal filesystem.
- D. Share the build cache between them.
  - 해설: Share the build cache between them.
✅ 내 답: Mount the same volume into both containers.
설명: Sharing data between containers is best done with a shared volume or another shared persistent storage mechanism.