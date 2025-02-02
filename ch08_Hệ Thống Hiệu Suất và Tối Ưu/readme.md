# Thành phần Stamina trong Unreal Engine

## Tổng quan
Thành phần Stamina trong Unreal Engine là một thành phần tùy chỉnh quản lý sức bền của nhân vật. Nó thường được sử dụng trong các trò chơi để kiểm soát các hành động như chạy nhanh, nhảy và các hoạt động khác tiêu tốn sức bền.

## Tính năng chính
- **Quản lý Stamina**: Theo dõi mức stamina hiện tại của nhân vật.
- **Tiêu thụ Stamina**: Giảm stamina dựa trên các hành động của nhân vật.
- **Hồi phục Stamina**: Tự động hồi phục stamina theo thời gian khi không sử dụng.
- **Cạn kiệt Stamina**: Xử lý các hiệu ứng khi stamina bị cạn kiệt hoàn toàn.

## Chi tiết triển khai
### Thuộc tính
- **MaxStamina**: Giá trị stamina tối đa mà nhân vật có thể có.
- **CurrentStamina**: Giá trị stamina hiện tại của nhân vật.
- **StaminaDrainRate**: Tốc độ tiêu thụ stamina trong các hành động.
- **StaminaRegenRate**: Tốc độ hồi phục stamina khi không sử dụng.

### Hàm
- **ConsumeStamina(float Amount)**: Giảm stamina hiện tại theo giá trị được chỉ định.
- **RegenerateStamina(float DeltaTime)**: Tăng stamina hiện tại dựa trên tốc độ hồi phục và thời gian delta.
- **IsStaminaDepleted()**: Kiểm tra xem stamina hiện tại có bằng không hay không.

### Ví dụ sử dụng
```cpp
void UStaminaComponent::ConsumeStamina(float Amount)
{
    CurrentStamina = FMath::Clamp(CurrentStamina - Amount, 0.0f, MaxStamina);
}

void UStaminaComponent::RegenerateStamina(float DeltaTime)
{
    if (CurrentStamina < MaxStamina)
    {
        CurrentStamina += StaminaRegenRate * DeltaTime;
        CurrentStamina = FMath::Clamp(CurrentStamina, 0.0f, MaxStamina);
    }
}

bool UStaminaComponent::IsStaminaDepleted() const
{
    return CurrentStamina <= 0.0f;
}
```

## Tích hợp
Để tích hợp thành phần Stamina vào nhân vật:
1. Thêm thành phần vào lớp nhân vật.
2. Liên kết tiêu thụ stamina với các hành động của nhân vật (ví dụ: chạy nhanh).
3. Cập nhật hồi phục stamina trong hàm tick của nhân vật.

```cpp
// Trong lớp nhân vật
UStaminaComponent* StaminaComponent;

// Trong hàm tick của nhân vật
StaminaComponent->RegenerateStamina(DeltaTime);
```

## Kết luận
Thành phần Stamina là một phần quan trọng trong việc quản lý nhân vật trong Unreal Engine, cung cấp một hệ thống mạnh mẽ để xử lý các cơ chế liên quan đến stamina trong các trò chơi.