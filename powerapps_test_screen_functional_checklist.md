# Power Apps Test Screen Functional Checklist

Yes — here is the **functional-only checklist** from your latest test screen, grouped by area.

## Screen

- `OnVisible`  
  Initializes screen state:
  ```powerfx
  UpdateContext({varShowContainer: "table"})
  ```

## Table

- `Items`  
  Binds the table directly to the SharePoint list:
  ```powerfx
  'CV_ListOfPersons-TEST'
  ```

- Added/defined columns:
  - `ID`
  - `UseCaseManager`
  - `LauchEngineer` shown with header text **Launch Engineer**  
  
## Form

- `DataSource`
  ```powerfx
  'CV_ListOfPersons-TEST'
  ```

- `Item`  
  Current record comes from the selected table row:
  ```powerfx
  tblTest.Selected
  ```

- `Visible` on the form container  
  Form is shown only in edit mode:
  ```powerfx
  varShowContainer = "form-edit"
  ```

- `OnSuccess`  
  After save, reset form and return to table view:
  ```powerfx
  ResetForm(frmTest);
  UpdateContext({varShowContainer: "table"})
  ```

## ID card

- `DataField`
  ```powerfx
  "ID"
  ```
- `Default`
  ```powerfx
  ThisItem.ID
  ```

- Inner value control:
  - `DisplayMode = DisplayMode.View`
  - `Value = Parent.Default`  
  This makes the SharePoint system ID visible but read-only.

## Person cards

For both Person ComboBoxes:

- `Items`
  ```powerfx
  Office365Users.SearchUser({searchTerm: Self.SearchText, top: 10})
  ```
- `DefaultSelectedItems`
  ```powerfx
  [Parent.Default]
  ```
- `DisplayMode`
  ```powerfx
  Parent.DisplayMode
  ```

For the Person DataCard `Update`, you are explicitly shaping the SharePoint Person value instead of relying on default behavior:

```powerfx
If(
    IsBlank(...Selected),
    Blank(),
    {
        '@odata.type': "#Microsoft.Azure.Connectors.SharePoint.SPListExpandedUser",
        Claims: ...,
        DisplayName: ...,
        Email: ...
    }
)
```

This is the key functional pattern for saving a Person field correctly.

## Buttons

### New button
- `DisplayMode`
  ```powerfx
  If(varShowContainer = "table", DisplayMode.Edit, DisplayMode.Disabled)
  ```
- `OnSelect`
  ```powerfx
  NewForm(frmTest);
  UpdateContext({varShowContainer: "form-edit"})
  ```
  
### Edit button
- `DisplayMode`
  ```powerfx
  If(!IsBlank(tblTest.Selected), DisplayMode.Edit, DisplayMode.Disabled)
  ```
- `OnSelect`
  ```powerfx
  UpdateContext({varShowContainer: "form-edit"})
  ```
  
### Save button
- `DisplayMode`
  ```powerfx
  If(
      varShowContainer = "form-edit" && frmTest.Unsaved && frmTest.Valid,
      DisplayMode.Edit,
      DisplayMode.Disabled
  )
  ```
- `OnSelect`
  ```powerfx
  SubmitForm(frmTest)
  ```
  
### Cancel button
- `DisplayMode`
  Enabled only in form mode
- `OnSelect`
  ```powerfx
  ResetForm(frmTest);
  UpdateContext({varShowContainer: "table"})
  ```
