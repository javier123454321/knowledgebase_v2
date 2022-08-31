- [[Gratitude List]]
- [[Quick Capture]]
    - Storage slots for Solidity
        - Storage Slots
            - 32 Bytes
        - Uint 128 16 bytes, uint 96: 12 bytes, uint64: 8bytes
        - Address: 20bytes
            - ```javascript
struct Record{	
    address wallet; //20/32bytes
    uint256 number; //32/bytes
}
struct Record{
    address wallet; //20/32bytes
    uint96 number; //23/bytes
  	//now only one slot is needed
}```