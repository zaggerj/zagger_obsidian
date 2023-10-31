---

mindmap-plugin: basic

---

# wdi.ReassemblerFactory

## getPacketReassembler
- this.getSizeDefiner();
- this.getPacketController(sD, socketQ);
- return new wdi.PacketReassembler({packetController: pC});

## getSizeDefiner
- new wdi.SizeDefiner();

## getPacketController
- return new wdi.PacketController({socketQ: socketQ, sizeDefiner: sizeDefiner});