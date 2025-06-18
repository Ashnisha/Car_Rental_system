# 🚗 Car Rental System

Explore the world of car rentals with the **Car Rental System**, a Java-based console application that combines learning and simulation. 🌟

## Features

🚀 Rent a Car: Experience the ease of renting cars through an interactive console.
🔁 Return a Car: Effortlessly return previously rented cars and update availability.
👥 Customer Management: Add new customers and maintain customer records.
🚗 Car Management: Manage cars, brands, models, and pricing details.
📝 Rental History: Keep track of rentals, customers, and rental durations.

## Contributions Welcome! 🎉

Contribute to the project's growth. Open issues, submit pull requests, and collaborate with the community.

## Future Roadmap 🛤️

🤝 Support multiple customers renting the same car simultaneously.
⏰ Implement date-based pricing adjustments.
🎨 Develop a graphical user interface (GUI) for enhanced user experience.

---

Feel the thrill of renting and returning cars while mastering OOP concepts. Dive into the Car Rental System and drive your learning forward! 🚗💨


---
- name: Deploy keystore files and set permissions for UK UAT
  hosts: all
  become: true
  tasks:

    - name: Ensure keystore directory exists
      file:
        path: /opt/juniper/keystore
        state: directory
        mode: '0775'

    - name: Copy truststore.jks
      copy:
        src: truststore.jks
        dest: /opt/juniper/keystore/truststore.jks
        mode: '0775'

    - name: Copy master_key.txt
      copy:
        src: master_key.txt
        dest: /opt/juniper/keystore/master_key.txt
        mode: '0775'

    - name: Create telemetry store directory with drwxr-x--- permission
      file:
        path: /opt/juniper/applicationcode/devops/build/juniper-stream-kafka-telemetry/store
        state: directory
        owner: appuser        # 🔁 Replace with actual owner
        group: appgroup       # 🔁 Replace with group needing access
        mode: '0750'

    - name: Ensure log directory is readable by other users
      file:
        path: /var/log/juniper/
        state: directory
        mode: '0755'
      tags: log-permission
