##
GENERACION AUTOMATICA DE DOCUMENTACION TECNICA
##

```
@RestController
@RequestMapping("/api/v1/deliveries")
@RequiredArgsConstructor
@Tag(name = "Deliveries", description = "API for deliveries management")
public class DeliveryController {

    private final IDeliveryService deliveryService;

    @Operation(summary = "Create a new delivery")
    @ApiResponses({
            @ApiResponse(responseCode = "201", description = "Delivery created successfully"),
            @ApiResponse(responseCode = "400", description = "Invalid input")
    })
    @PostMapping(consumes = MediaType.MULTIPART_FORM_DATA_VALUE)
    public ResponseEntity<DeliveryResponseDto> createDelivery(
            @ModelAttribute CreateDeliveryRequestDto dto) {

        DeliveryResponseDto saved = deliveryService.save(dto);
        return ResponseEntity.status(HttpStatus.CREATED).body(saved);
    }

    @Operation(summary = "Get a delivery by its ID")
    @ApiResponses({
            @ApiResponse(responseCode = "200", description = "Delivery found"),
            @ApiResponse(responseCode = "404", description = "Delivery not found")
    })
    @GetMapping("/{id}")
    public ResponseEntity<DeliveryResponseDto> getDeliveryById(@PathVariable Long id) {
        return ResponseEntity.ok(deliveryService.findDtoById(id));
    }

    @Operation(summary = "Get a paginated list of deliveries")
    @ApiResponses({ @ApiResponse(responseCode = "200", description = "Successfully retrieved list") })
    @PostMapping("/paginate")
    public ResponseEntity<Page<?>> getPaginatedDeliveries(@RequestBody PaginationModel paginationModel) {
        return ResponseEntity.ok(deliveryService.paginationProjections(paginationModel));
    }

    @Operation(summary = "Update an existing delivery")
    @ApiResponses({
            @ApiResponse(responseCode = "200", description = "Delivery updated successfully"),
            @ApiResponse(responseCode = "404", description = "Delivery not found"),
            @ApiResponse(responseCode = "400", description = "Invalid input")
    })
    @PutMapping(value = "/{id}", consumes = MediaType.MULTIPART_FORM_DATA_VALUE)
    public ResponseEntity<DeliveryResponseDto> updateDelivery(
            @PathVariable Long id,
            @ModelAttribute UpdateDeliveryRequestDto dto) {

        DeliveryResponseDto updated = deliveryService.update(id, dto);
        return ResponseEntity.ok(updated);
    }

    @Operation(summary = "Delete a delivery by its ID")
    @ApiResponses({
            @ApiResponse(responseCode = "204", description = "Delivery deleted successfully"),
            @ApiResponse(responseCode = "404", description = "Delivery not found")
    })
    @DeleteMapping("/{id}")
    public ResponseEntity<Void> deleteDelivery(@PathVariable Long id) {
        deliveryService.delete(id);
        return ResponseEntity.noContent().build();
    }

    // Estos dos endpoints siguen igual si quieres devolver entidades planas
    @Operation(summary = "Get all deliveries")
    @ApiResponses({ @ApiResponse(responseCode = "200", description = "Successfully retrieved list") })
    @GetMapping
    public ResponseEntity<List<DeliveryResponseDto>> getAllDeliveries() {
        // recomiendan devolver DTOs listos (no entidades)
        List<Delivery> deliveries = deliveryService.findAll();
        List<DeliveryResponseDto> dtos = deliveries.stream()
                .map(d -> deliveryService.findDtoById(d.getId())) // compone DTO con medias
                .collect(Collectors.toList());
        return ResponseEntity.ok(dtos);
    }

    @Operation(summary = "Get deliveries by title")
    @ApiResponses({ @ApiResponse(responseCode = "200", description = "Successfully retrieved list") })
    @GetMapping("/by-title/{title}")
    public ResponseEntity<List<DeliveryResponseDto>> getDeliveriesByTitle(@PathVariable String title) {
        List<Delivery> deliveries = deliveryService.findByTitle(title);
        List<DeliveryResponseDto> dtos = deliveries.stream()
                .map(d -> deliveryService.findDtoById(d.getId()))
                .collect(Collectors.toList());
        return ResponseEntity.ok(dtos);
    }
}
```