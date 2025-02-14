# Gestion des Utilisateurs

## Modèle de Données

```java
@Entity
public class User {
    @Id
    private UUID id;
    private String pseudonyme;
    @ElementCollection
    private Set<UUID> contacts; 
    @Transient
    private PublicKey pubKey;
}
```

## Gestion des Profils

### Anonymat et Sécurité
- Pas de numéro de téléphone requis
- Pseudonymes uniques mais modifiables
- Stockage minimal des données personnelles

### Synchronisation Multi-Devices
```java
@Service
public class DeviceSyncService {
    public void syncUserData(UUID userId, DeviceInfo device) {
        // Chiffrement des données pour le device
        byte[] encryptedData = encryptForDevice(
            userData, device.getPublicKey()
        );
        // Envoi via WebSocket
        wsService.sendToDevice(device.getId(), encryptedData);
    }
}
```

## Gestion des Contacts

### Structure des Contacts
```java
public class Contact {
    private UUID userId;
    private String displayName;
    private byte[] publicKeyFingerprint;
    private ContactStatus status;
}
```

### Sécurité des Contacts
- Vérification des fingerprints
- Alerte en cas de changement de clé
- Blocage et signalement possibles

## Confidentialité

### Paramètres de Confidentialité
| Paramètre | Options | Par défaut |
|-----------|---------|------------|
| Visibilité profil | Tous/Contacts/Personne | Contacts |
| Statut en ligne | Visible/Masqué | Visible |
| Dernière vue | Visible/Masquée | Masquée |

### Contrôles d'Accès
```java
@PreAuthorize("@privacyService.canViewProfile(#targetUserId)")
public UserProfile getProfile(UUID targetUserId) {
    return userRepository.findProfileById(targetUserId)
        .map(this::filterSensitiveData)
        .orElseThrow(UserNotFoundException::new);
}
