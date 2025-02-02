
## Điều Khiển Nhân Vật Trong Unreal Engine Bằng C++

Trong phần này, chúng ta sẽ học cách điều khiển nhân vật trong Unreal Engine bằng C++.

## Bước 1: Tạo Dự Án Mới
Mở Unreal Engine và tạo một dự án mới với template "Third Person". Đặt tên dự án và chọn vị trí lưu trữ phù hợp.

## Bước 2: Tạo Lớp Nhân Vật
Tạo một lớp C++ mới kế thừa từ `ACharacter`. Đặt tên lớp là `MyCharacter`.

```cpp
#include "GameFramework/Character.h"
#include "MyCharacter.generated.h"

UCLASS()
class AMyCharacter : public ACharacter {
    GENERATED_BODY()

public:
    AMyCharacter();

protected:
    virtual void SetupPlayerInputComponent(class UInputComponent* PlayerInputComponent) override;

    void MoveForward(float Value);
    void MoveRight(float Value);
};
```

## Bước 3: Định Nghĩa Hàm Di Chuyển
Trong file `.cpp`, định nghĩa các hàm di chuyển để xử lý đầu vào từ người chơi.

```cpp
#include "MyCharacter.h"

AMyCharacter::AMyCharacter() {
    PrimaryActorTick.bCanEverTick = true;
}

void AMyCharacter::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent) {
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAxis("MoveForward", this, &AMyCharacter::MoveForward);
    PlayerInputComponent->BindAxis("MoveRight", this, &AMyCharacter::MoveRight);
}

void AMyCharacter::MoveForward(float Value) {
    if (Value != 0.0f) {
        AddMovementInput(GetActorForwardVector(), Value);
    }
}

void AMyCharacter::MoveRight(float Value) {
    if (Value != 0.0f) {
        AddMovementInput(GetActorRightVector(), Value);
    }
}
```

## Bước 4: Cấu Hình Input
Mở `Project Settings` và cấu hình các trục điều khiển cho "MoveForward" và "MoveRight". Điều này bao gồm việc gán các phím hoặc trục điều khiển từ bàn phím hoặc gamepad.

1. Đi tới `Edit` > `Project Settings`.
2. Trong mục `Engine` > `Input`, thêm các trục mới:
    - `MoveForward` với `W` và `S` cho giá trị 1 và -1 tương ứng.
    - `MoveRight` với `A` và `D` cho giá trị -1 và 1 tương ứng.

## Kết Luận
Bạn đã học cách tạo và điều khiển nhân vật trong Unreal Engine bằng C++. Bạn có thể mở rộng thêm các tính năng như va chạm, hoạt ảnh, và nhiều hơn nữa để làm cho trò chơi của bạn thú vị hơn. Hãy thử nghiệm và sáng tạo để tạo ra những trải nghiệm độc đáo cho người chơi.
