# PBX Admin Guide: Connecting to a Remote RF-Link Node (IAX Extension, FreePBX 17)

This guide explains how to create an IAX2 extension in FreePBX 17 so your PBX can connect to a remote RF-Link node (where the node acts as the Asterisk server).

---

## 1. Gather Required Information

Ensure you have the following details from the RF-Link node owner:
- **Callsign:** The callsign of the individual or club of the RF-link owner. 
- **Username:** The identifier for the RF-Link node IAX extension. Normally the callsign.
- **Password:** The secret/password for this extension. At least 10 digits. STRONG PASSWORD!
- **IAX Port:** The UDP port for IAX (usually 4569, or a custom port if required by the RF-Link owner).
- **IAX String:** The string provided by the RF-Link owner to configure the extension. [IAX2 String Generator](https://freestareverywhere.com/apps/iax2string-generator/)

---

## 2. Understand the Dial String Format

The RF-Link owner will provide a dial string in the following format:

```text
IAX2/USERNAME:PASSWORD@NODE-HOSTNAME:PORT/NODE
```

**Example:**
```text
IAX2/freestar:passw0rd@40071.nodes.allstarlink.org:4569/40071
```

**Components:**
- `freestar` = Username (normally callsign of node owner or club call)
- `passw0rd` = Password/secret
- `40071.nodes.allstarlink.org` = Node's public DNS or IP address
- `4569` = IAX port (default is 4569)
- `/40071` = Desired AllStar Node number

You can generate this string using the [IAX2 String Generator](https://freestareverywhere.com/apps/iax2string-generator/).

---

## 3. RF-Link Owner Provides Dial String

To dial the RF-Link node from FreePBX, use a dial string is used in the following format:

```text
IAX2/USERNAME:PASSWORD@NODE-HOSTNAME:PORT/NODE
```
**For example:**
```text
IAX2/freestar:passw0rd@40071.nodes.allstarlink.org:4580/40071
```
- Replace `freestar` with the **username**. Normally callsign of node owner or club call.
- Replace `passw0rd` with the **password/secret**.
- Replace `40071.nodes.allstarlink.org` with the **node’s public DNS** or IP.
- Replace `4580` with the **IAX port** (if not the default `4569`).
- Replace the final `/40071` with the **desired AllStar Node** on the RF-Link node (typically its node number or private node number).

You can use this dial string wherever you configure IAX extensions, outbound routes, custom extensions, or follow-me destinations in FreePBX to reach the RF-Link node.
Direct the RF-Link applicant to provide dial string using the Dial String Generator [IAX2 String Generator](https://freestareverywhere.com/apps/iax2string-generator/)

1. Go to **Applications > Extensions**
2. Click **Add Extension** > **Add IAX2 Extension**

### General Tab Configuration:

- **User Extension:** Enter a unique extension number (e.g., `8001`)
- **Display Name:** Enter a descriptive name (e.g., `RF-Link Node`)
- **Secret:** Enter the password provided by the RF-Link owner
- **Outbound CallerID:** Leave blank or set as desired

### Advanced Tab Configuration:

3. Click on the **Advanced** tab
4. Configure the following settings:

- **Transfer:** `no`
- **Host:** Enter the node's hostname (e.g., `40071.nodes.allstarlink.org`) or IP address as provided by the RF-Link owner
- **Port:** Enter the IAX port (e.g., `4569`, or custom port specified by the RF-Link owner)
- **Qualify:** `yes`
- **Disallow:** `all`
- **Allow:** `ulaw`

### Dial Configuration:

5. In the **Dial** field, enter the dial string provided by the RF-Link owner:
   ```text
   IAX2/USERNAME:PASSWORD@NODE-HOSTNAME:PORT/NODE
   ```
   **Example:**
   ```text
   IAX2/freestar:passw0rd@40071.nodes.allstarlink.org:4569/40071
   ```

6. Click **Submit** and then **Apply Config**

### Firewall Considerations:

If your PBX is behind NAT/firewall, ensure outbound UDP traffic to the node's IP and IAX port is permitted.

---

## 4. Test the Connection

1. Use the Asterisk CLI to verify the connection:
   ```bash
   asterisk -rx "iax2 show peers"
   ```
   - Look for your new RF-Link extension in the list
   - Status should show "OK" if the node is reachable (BLF will be green)
   - If the node is "UNKNOWN" or "OFFLINE", the BLF will be grey

2. Test calling the extension:
   - Dial the extension from a SIP phone or another extension
   - The call should route to the RF-Link node and trigger its dialplan

---

## 5. Troubleshooting

- **Connection Issues:**
  - Double-check username, password, port, hostname, and extension match the node configuration
  - Ensure your PBX can reach the RF-Link node's public IP/DNS (check firewall/NAT rules)
  
- **Authentication Errors:**
  - If you see "no authority" or "authentication failed," verify credentials are correctly entered
  
- **Debugging:**
  - Use Asterisk logs for detailed information:
    ```bash
    asterisk -rvv
    ```

---

## 6. Support

For further help, contact: M0VUB
