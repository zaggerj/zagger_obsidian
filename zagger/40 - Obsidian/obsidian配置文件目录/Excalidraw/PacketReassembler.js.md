---

mindmap-plugin: basic

---

# wdi.PacketReassembler

## init
- setListeners
    - this.packetController.addListener('chunkComplete'
        - 'spicePacket'
            - this.fire('packetComplete', rawMessage);
    - this.packetController.addListener('error',
        - this.fire('error', e);
- this.statusToString
- this.packetController