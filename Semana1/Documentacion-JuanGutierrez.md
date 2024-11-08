# Documentación Semanal

## Nombre: Juan Gutierrez
## Ciclo: Tercero

### Ani-react-native

#### Login Form:

```
const passwordRef = useRef<TextInput>(null);
// Se añadió esta referencia para enfocar el campo "password" después de completar el campo "Email".

<InputField
    title="Email"
    value={institutionalEmail}
    onChangeText={(text) => setInstitutionalEmail(text)}
    onSubmitEditing={() => passwordRef.current?.focus()} // Se añadió este State para realizar el salto de campo
    returnKeyType="next" 
/>
                    
<InputField
title="Password"
password
value={password}
onChangeText={(text) => setPassword(text)}
ref={passwordRef} 
returnKeyType="done" 
/>

```

#### Room/Index

```
const fadeAnim = new Animated.Value(0); 
                            
                        
    Animated.timing(fadeAnim, {
        toValue: 1, 
        duration: 250, 
        useNativeDriver: true,
        }).start();

    return (
        <Animated.View style={{ opacity: fadeAnim }}>
            <Link key={index} href={`/rooms/${item.roomId}`} asChild>
        <Pressable>
        <RoomItem {...item} />
        </Pressable>
        </Link>
        </Animated.View>
    );

// Se añadió este código para crear un efecto de desvanecimiento al renderizar los rooms, usando la API de animación de React Native.


```

### Ani-web-app

#### RoomCreate

```
 else if (mode === 'edit' && initialValues?.roomId) {
                console.log("Updating room with ID:", initialValues.roomId); 
                console.log("Updating room with data:", values); 
                const updatedRoom = await apiService.update<Room>(roomsApi, initialValues.roomId, values);
                onEdit(updatedRoom);
                notificationService.success("Room Updated", "The room has been updated successfully.");
        }

// Este código cambia el estado del drawer a modo "edit" cuando mode no es "create" y hay un roomId definido.

```
#### RoomList

```

const handleEdit = async (values: Room) => {
    try {
        console.log('Room edited:', values);
        closeDrawer();
    } catch (error) {
        console.error('Error editing room:', error);
    }
};

 <RoomCreate
    onEdit={handleEdit} 
/>

// Se creó la función handleEdit para manejar la edición de un room, y se pasó a RoomCreate.

```

#### Room-Topic Drawer

```
const handleSwitchChange = async (checked: boolean, topic: Topic) => {
        try {
            await apiService.update(topicsApi, topic.topicId, { enabled: checked });
            refetch();
        } catch (error) {
            console.error('Error updating topic status:', error);
        }
    };

// Se creó handleSwitchChange para editar el estado de un topic usando un switch (componente de Ant Design).

```

```

{
        title: "Enabled",
        render: (_text, record: Topic) => (
            <Switch
                checked={record.enabled}
                onChange={(checked) => handleSwitchChange(checked, record)} // maneja el cambio de estado
            />
        ),
    },

// Se añadió un Switch en la columna "Enabled" para activar o desactivar el estado de un topic.


```

- Se realizaron algunas reuniones al momento de desarrollar las tareas asignadas (presentes en el product backlog) para coordinar algunas tareas las cuales nos asignaron a 2 o más compañeros.
- Se realizó Pair Programming para completar algunas tareas de manera más eficiente.
- Se realizó el despliegue de las tareas asignadas, en la cual se tomaron notas sobre los bugs y mejoras que se pueden implemenar en el proyecto.
- Se realizó una reunción de PrePlanning para establecer los equipos.
- Se realizó el sprint planning para establecer las tereas que iba a tener cada funcionalidad.
